# Config

[TOC]

Adhearsion 2.0 brings a brand new configuration system which is environment-aware, self-describing and both programatically- and human-inspectable. The application's central configuration system holds settings for adhearsion core as well as all 3rd-party or local plugins.

## Viewing current/default config

In order to visually inspect the current state of the application's configuration, run `rake config:show`, like so:

<pre class="terminal">

$ rake config:show

Adhearsion configured environment: development

Adhearsion.config do |config|

  # ******* Configuration for platform **************

<span class="ansi33">  # </span><span class="ansi32">Active environment. Supported values: development, production, staging, test [AHN_PLATFORM_ENVIRONMENT]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">environment       </span><span class="ansi33"> = </span><span class="ansi36">:development</span>

<span class="ansi33">  # </span><span class="ansi32">Folder to include the own libraries to be used. Adhearsion loads any ruby file</span>
<span class="ansi33">  # </span><span class="ansi32">located into this folder during the bootstrap process. Set to nil if you do not</span>
<span class="ansi33">  # </span><span class="ansi32">want these files to be loaded. This folder is relative to the application root folder. [AHN_PLATFORM_LIB]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">lib               </span><span class="ansi33"> = </span><span class="ansi36">"lib"</span>

<span class="ansi33">  # </span><span class="ansi32">Log configuration [AHN_PLATFORM_LOGGING]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">logging</span>

<span class="ansi33">  # </span><span class="ansi32">A log formatter to apply to all active outputters. If nil, the Adhearsion default formatter will be used. [AHN_PLATFORM_LOGGING_FORMATTER]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">logging.formatter </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">Supported levels (in increasing severity) -- :trace &lt; :debug &lt; :info &lt; :warn &lt; :error &lt; :fatal [AHN_PLATFORM_LOGGING_LEVEL]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">logging.level     </span><span class="ansi33"> = </span><span class="ansi36">:debug</span>

<span class="ansi33">  # </span><span class="ansi32">An array of log outputters to use. The default is to log to stdout and log/adhearsion.log.</span>
<span class="ansi33">  # </span><span class="ansi32">Each item must be either a string to use as a filename, or a valid Logging appender (see http://github.com/TwP/logging) [AHN_PLATFORM_LOGGING_OUTPUTTERS]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">logging.outputters</span><span class="ansi33"> = </span><span class="ansi36">["log/adhearsion.log"]</span>

<span class="ansi33">  # </span><span class="ansi32">Adhearsion process name, useful to make it easier to find in the process list</span>
<span class="ansi33">  # </span><span class="ansi32">Pro tip: set this to your application's name and you can do "killall myapp"</span>
<span class="ansi33">  # </span><span class="ansi32">Does not work under JRuby. [AHN_PLATFORM_PROCESS_NAME]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">process_name      </span><span class="ansi33"> = </span><span class="ansi36">"ahn"</span>

<span class="ansi33">  # </span><span class="ansi32">Adhearsion application root folder [AHN_PLATFORM_ROOT]</span>
<span class="ansi33">  config.platform.</span><span class="ansi37">root              </span><span class="ansi33"> = </span><span class="ansi36">"/Users/bklang/src/adhearsion-website/docs/artifacts/80eddf8bb53eddb83f89b24ae751ba75/source/getting-started/myapp"</span>

  # ******* Configuration for punchblock **************

<span class="ansi33">  # </span><span class="ansi32">The domain at which to address calls [AHN_PUNCHBLOCK_CALLS_DOMAIN]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">calls_domain      </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">The amount of time to wait for a connection [AHN_PUNCHBLOCK_CONNECTION_TIMEOUT]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">connection_timeout</span><span class="ansi33"> = </span><span class="ansi36">60</span>

<span class="ansi33">  # </span><span class="ansi32">The default TTS voice to use. [AHN_PUNCHBLOCK_DEFAULT_VOICE]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">default_voice     </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">Host punchblock needs to connect (where rayo/asterisk/freeswitch is located) [AHN_PUNCHBLOCK_HOST]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">host              </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">The media engine to use. Defaults to platform default. [AHN_PUNCHBLOCK_MEDIA_ENGINE]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">media_engine      </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">The domain at which to address mixers [AHN_PUNCHBLOCK_MIXERS_DOMAIN]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">mixers_domain     </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">Authentication credentials [AHN_PUNCHBLOCK_PASSWORD]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">password          </span><span class="ansi33"> = </span><span class="ansi36">"1"</span>

<span class="ansi33">  # </span><span class="ansi32">Platform punchblock shall use to connect to the Telephony provider. Currently supported values:</span>
<span class="ansi33">  # </span><span class="ansi32">- :xmpp</span>
<span class="ansi33">  # </span><span class="ansi32">- :asterisk</span>
<span class="ansi33">  # </span><span class="ansi32">- :freeswitch [AHN_PUNCHBLOCK_PLATFORM]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">platform          </span><span class="ansi33"> = </span><span class="ansi36">:xmpp</span>

<span class="ansi33">  # </span><span class="ansi32">Port punchblock needs to connect [AHN_PUNCHBLOCK_PORT]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">port              </span><span class="ansi33"> = </span><span class="ansi36">5222</span>

<span class="ansi33">  # </span><span class="ansi32">The number of times to (re)attempt connection to the server [AHN_PUNCHBLOCK_RECONNECT_ATTEMPTS]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">reconnect_attempts</span><span class="ansi33"> = </span><span class="ansi36">Infinity</span>

<span class="ansi33">  # </span><span class="ansi32">Delay between connection attempts [AHN_PUNCHBLOCK_RECONNECT_TIMER]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">reconnect_timer   </span><span class="ansi33"> = </span><span class="ansi36">5</span>

<span class="ansi33">  # </span><span class="ansi32">The root domain at which to address the server [AHN_PUNCHBLOCK_ROOT_DOMAIN]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">root_domain       </span><span class="ansi33"> = </span><span class="ansi36">nil</span>

<span class="ansi33">  # </span><span class="ansi32">Authentication credentials [AHN_PUNCHBLOCK_USERNAME]</span>
<span class="ansi33">  config.punchblock.</span><span class="ansi37">username          </span><span class="ansi33"> = </span><span class="ansi36">"usera@127.0.0.1"</span>

end
</pre>

This output shows the currently active configuration as a combination of default values and overrides. It also provides brief documentation relating to each option.

The active configuration is derived from the default values for each key, overridden first by the on-disk configuration (in `config/adhearsion.rb`) and then by any provided in the application's environment (see below). Thus the order of precedence is:

* Environment Variables
* Hard-coded configuration
* Default values

## Configuring Adhearsion & Plugins

In order to override an application's settings, you can set new values in `config/adhearsion.rb`. To get started, you can actually copy-paste the output from `rake config:show`, and modify it for your needs. The syntax of the config file is hopefully self-explanatory:

```ruby
# encoding: utf-8

Adhearsion.config do |config|

  # Centralized way to specify any Adhearsion platform or plugin configuration
  # - Execute rake config:show to view the active configuration values
  #
  # To update a plugin configuration you can write either:
  #
  #    * Option 1
  #        Adhearsion.config.<plugin-name> do |config|
  #          config.<key> = <value>
  #        end
  #
  #    * Option 2
  #        Adhearsion.config do |config|
  #          config.<plugin-name>.<key> = <value>
  #        end

  config.development do |dev|
    dev.platform.logging.level = :debug
  end

  ##
  # Use with Rayo (eg Voxeo PRISM)
  #
  # config.punchblock.username = "" # Your XMPP JID for use with Rayo
  # config.punchblock.password = "" # Your XMPP password

  ##
  # Use with Asterisk
  #
  # config.punchblock.platform = :asterisk # Use Asterisk
  # config.punchblock.username = "" # Your AMI username
  # config.punchblock.password = "" # Your AMI password
  # config.punchblock.host = "127.0.0.1" # Your AMI host

  ##
  # Use with FreeSWITCH
  #
  # config.punchblock.platform = :freeswitch # Use FreeSWITCH
  # config.punchblock.password = "" # Your Inbound EventSocket password
  # config.punchblock.host = "127.0.0.1" # Your IES host
end

Adhearsion::Events.draw do

  # Register global handlers for events
  #
  # eg. Handling Punchblock events
  # punchblock do |event|
  #   ...
  # end
  #
  # eg Handling PeerStatus AMI events
  # ami name: 'PeerStatus' do |event|
  #   ...
  # end
  #
end

Adhearsion.router do

  #
  # Specify your call routes, directing calls with particular attributes to a controller
  #

  route 'default', SimonGame
end
```

## Storing configuration in the environment

It is considered bad practice to store sensitive data (such as database credentials or API keys) in source control, or to mix environment-specific configuration with your application's standard behaviour. You can read more about this philosophy as part of the [twelve-factor manifesto](http://www.12factor.net/config). Adhearsion allows you to configure any part of the core system or plugins using environment variables. The output from "rake config:show" includes a capitalised reference to the environment variable name corresponding to each configuration key.

For example, to override the punchblock username and password at runtime, you may do this:

<pre class="terminal">

AHN_PUNCHBLOCK_USERNAME=testuser AHN_PUNCHBLOCK_PASSWORD=foobar ahn start .
</pre>

<div class='docs-progress-nav'>
  <span class='back'>
    Back to <a href="/docs/routing">Routing</a>
  </span>
  <span class='forward'>
    Continue to <a href="/docs/events">Events</a>
  </span>
</div>
