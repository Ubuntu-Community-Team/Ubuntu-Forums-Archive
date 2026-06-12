---
title: "Lucid: Cannot run a PHP file"
date: 2010-07-06
forum: General Help
---

### Post by fopetesl on 2010-07-06
Am attempting to upgrade from Breezy to Lucid but not without a lot of problems :(
The current brick wall is I cannot run a PHP file called from an HTM script.

First I can run [COLOR="Blue"]localhost/phpmyadmin[/COLOR] and can access/modify my MySQL database.
Second I can run [COLOR="Blue"]localhost/test.php[/COLOR] and see my PHP setup.
Third I can run a local swf file successfully but it does fail when attempting to access processsData.php with "Can't access network" which was almost always caused by a PHP syntax error.
I have run the php script through a PHP5 syntax checker with no error.
Fourth I can run an htm script```
<form action="processData.php" method="post">
  <p>
    <input name="hook" type="text" id="hook"> 
    Hook
</p>
  <p>
    <input name="parameter0" type="text" id="parameter0"> 
  p0</p>
  <p>
    <input name="parameter1" type="text" id="parameter1">

p1</p>
  <p>
    <input name="parameter2" type="text" id="parameter2">
p2</p>
  <p>
    <input name="parameter3" type="text" id="parameter3">
p3</p>
  <p>
    <input name="parameter4" type="text" id="parameter4">

p4</p>
  <p>
    <input name="parameter5" type="text" id="parameter5">
  p5</p>
  <p>
    <input name="parameter6" type="text" id="parameter6">
  p6</p>
  <p>

    <input name="parameter7" type="text" id="parameter7">
p7</p>
  <p>
    <input name="parameter8" type="text" id="parameter8">
  p8</p>
  <p>
    <input name="parameter9" type="text" id="parameter9">
  p9</p>

  <p>&nbsp; </p>
  <p>&nbsp;</p>
  <p>
    <input type="submit" name="Submit" value="Submit">
  </p>
</form>
```but I get "[COLOR="Red"]What should Firefox do with this file[/COLOR]?" when merely entering '1' in 'hook' and clicking 'Submit' :confused:

---

### Post by WorMzy on 2010-07-06
Where is processData.php stored, and how are you accessing it? You need to access it through your server (localhost), and your server needs to know that php files in whichever directory you're storing this file in should be processed.

Here's a guide to setting up apache, which I'm assuming you're using: [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

---

### Post by fopetesl on 2010-07-06
> **WorMzy said:**
> Where is processData.php stored, and how are you accessing it? You need to access it through your server (localhost), and your server needs to know that php files in whichever directory you're storing this file in should be processed.

Here's a guide to setting up apache, which I'm assuming you're using: [http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)WorMzy, thanks.
But I'm not trying to access processData.php through the browser.  It's 'called' from the Flash GUI.
Works fine in Breezy but stumbles in Lucid.
I've been through all the LAMP/APACHE/PHP/MySQL setups I can find and everything except this works fine.
I'll run through it all again in the morning - time for a beer now :)

---

### Post by WorMzy on 2010-07-06
So flash is processing the PHP? I'm not.. on good terms with flash, so I couldn't say what might be going wrong with it if it is. But the htm page needs to have the PHP processed, otherwise Firefox (and other browsers) will just see a text file with a PHP extension, not the html code that they're supposed to receive after the server has finished processing the php.

---

### Post by fopetesl on 2010-07-07
> **WorMzy said:**
> So flash is processing the PHP? I'm not.. on good terms with flash, so I couldn't say what might be going wrong with it if it is. But the htm page needs to have the PHP processed, otherwise Firefox (and other browsers) will just see a text file with a PHP extension, not the html code that they're supposed to receive after the server has finished processing the php.
Maybe missing the point here?
Can I spell it out?

Breezy 5.10 - everything works fine.
Flash GUI (not my creation - the coding is the pits for me) 'calls' processData.php which returns data according to the request.

The htm script (test.htm actually) does essentially the same as the Flash GUI.  Generated to test processData.php script and see the returned result(s).

Lucid 10.04 - not good.
Flash GUI and test.htm load OK.  Neither will sub-process processData.php - error "what to do..."

Note I can run PHP scripts from /var/www without a problem.

Both test.htm and processData.php are in /var/www/html

If breezy will run them from /var/www/html, why won't Lucid?

Edit: I moved the relevant files, (processData.php, test.htm & gui.swf), into [COLOR="Blue"]/var/www[/COLOR] but still get the same ".. [COLOR="Red"]what do do with this file[/COLOR].." message in Firefox :(

---

### Post by WorMzy on 2010-07-07
It still sounds like it's not processing processData.php to me, but if other PHP scripts work fine, then I don't know what to tell you. Maybe posting the contents of processData.php will help, but I'd expect it to load a blank page, or display a PHP error (if you have PHP error reporting turned on) if there was a problem with it, rather than asking the client what to do with it.

If it worked on Breezy, but not on Lucid, then maybe double check your apache's config again.

---

### Post by fopetesl on 2010-07-07
> **WorMzy said:**
> It still sounds like it's not processing processData.php to me, but if other PHP scripts work fine, then I don't know what to tell you. Maybe posting the contents of processData.php will help, but I'd expect it to load a blank page, or display a PHP error (if you have PHP error reporting turned on) if there was a problem with it, rather than asking the client what to do with it.

If it worked on Breezy, but not on Lucid, then maybe double check your apache's config again.
There is no attempt to access the PHP files so I'd not see any PHP error so posting the PHP file(s) wouldn't help elucidate since all I get is the Firefox query.

I've been checking through apache's configs all morning against internet suggestions and also attempting to compare against the old configs.
The comparison didn't help much since they're different versions of apache.
But you're right I think WorMzy, must be in the setup somewhere?

---

### Post by WorMzy on 2010-07-07
> There is no attempt to access the PHP files

There is. Definitely in test.htm: ```
<form _action="processData.php"_ method="post">
```
And if your flash file works how you've described, then it almost certainly makes a call to the PHP script too.

Are you positive that you can run php scripts? If you create a new file in /var/www called phptest.php and put in the following:
```
<?php phpinfo(); ?>
```
Does it work when it access it through [http://localhost/phptest.php]("http://localhost/phptest.php")? It should display something like this:
[[img]http://www.ubuntu-pics.de/thumb/97310/phpinfo_____namoroka_003_p84E8h.png[/img]](http://www.ubuntu-pics.de/bild/97310/phpinfo_____namoroka_003_p84E8h.png)

---

### Post by fopetesl on 2010-07-07
OK. Sorry. My poor syntax.
When I said "no attempt to access the PHP script" I should have said "[COLOR="Blue"]when test.htm attempts to access processData.php Firefox (or apache?) interrupts this access[/COLOR]". i.e. test.htm never gets to run processData.php.
A similar scenario with the Flash GUI I guess.

To remind you about my original post> First I can run [COLOR="Blue"]localhost/phpmyadmin[/COLOR] and can access/modify my MySQL database.
Second I can run [COLOR="Blue"]localhost/test.php[/COLOR] and see my PHP setup.test.php:```
~# cat /var/www/test.php 
<?php phpinfo();?>
```

---

### Post by WorMzy on 2010-07-07
Ah, right.

I can only assume that there is a problem with your config then.
Have a look at your php.ini, here's mine for comparison:
```
[PHP]

;;;;;;;;;;;;;;;;;;;
; About php.ini   ;
;;;;;;;;;;;;;;;;;;;
; PHP's initialization file, generally called php.ini, is responsible for
; configuring many of the aspects of PHP's behavior.

; PHP attempts to find and load this configuration from a number of locations.
; The following is a summary of its search order:
; 1. SAPI module specific location.
; 2. The PHPRC environment variable. (As of PHP 5.2.0)
; 3. A number of predefined registry keys on Windows (As of PHP 5.2.0)
; 4. Current working directory (except CLI)
; 5. The web server's directory (for SAPI modules), or directory of PHP
; (otherwise in Windows)
; 6. The directory from the --with-config-file-path compile time option, or the
; Windows directory (C:\windows or C:\winnt)
; See the PHP docs for more specific information.
; http://php.net/configuration.file

; The syntax of the file is extremely simple.  Whitespace and Lines
; beginning with a semicolon are silently ignored (as you probably guessed).
; Section headers (e.g. [Foo]) are also silently ignored, even though
; they might mean something in the future.

; Directives following the section heading [PATH=/www/mysite] only
; apply to PHP files in the /www/mysite directory.  Directives
; following the section heading [HOST=www.example.com] only apply to
; PHP files served from www.example.com.  Directives set in these
; special sections cannot be overridden by user-defined INI files or
; at runtime. Currently, [PATH=] and [HOST=] sections only work under
; CGI/FastCGI.
; http://php.net/ini.sections

; Directives are specified using the following syntax:
; directive = value
; Directive names are *case sensitive* - foo=bar is different from FOO=bar.
; Directives are variables used to configure PHP or PHP extensions.
; There is no name validation.  If PHP can't find an expected
; directive because it is not set or is mistyped, a default value will be used.

; The value can be a string, a number, a PHP constant (e.g. E_ALL or M_PI), one
; of the INI constants (On, Off, True, False, Yes, No and None) or an expression
; (e.g. E_ALL & ~E_NOTICE), a quoted string ("bar"), or a reference to a
; previously set variable or directive (e.g. ${foo})

; Expressions in the INI file are limited to bitwise operators and parentheses:
; |  bitwise OR
; ^  bitwise XOR
; &  bitwise AND
; ~  bitwise NOT
; !  boolean NOT

; Boolean flags can be turned on using the values 1, On, True or Yes.
; They can be turned off using the values 0, Off, False or No.

; An empty string can be denoted by simply not writing anything after the equal
; sign, or by using the None keyword:

;  foo =         ; sets foo to an empty string
;  foo = None    ; sets foo to an empty string
;  foo = "None"  ; sets foo to the string 'None'

; If you use constants in your value, and these constants belong to a
; dynamically loaded extension (either a PHP extension or a Zend extension),
; you may only use these constants *after* the line that loads the extension.

;;;;;;;;;;;;;;;;;;;
; About this file ;
;;;;;;;;;;;;;;;;;;;
; PHP comes packaged with two INI files. One that is recommended to be used
; in production environments and one that is recommended to be used in
; development environments.

; php.ini-production contains settings which hold security, performance and
; best practices at its core. But please be aware, these settings may break
; compatibility with older or less security conscience applications. We
; recommending using the production ini in production and testing environments.

; php.ini-development is very similar to its production variant, except it's
; much more verbose when it comes to errors. We recommending using the
; development version only in development environments as errors shown to
; application users can inadvertently leak otherwise secure information.

;;;;;;;;;;;;;;;;;;;
; Quick Reference ;
;;;;;;;;;;;;;;;;;;;
; The following are all the settings which are different in either the production
; or development versions of the INIs with respect to PHP's default behavior.
; Please see the actual settings later in the document for more details as to why
; we recommend these changes in PHP's behavior.

; allow_call_time_pass_reference
;   Default Value: On
;   Development Value: Off
;   Production Value: Off

; display_errors
;   Default Value: On
;   Development Value: On
;   Production Value: Off

; display_startup_errors
;   Default Value: Off
;   Development Value: On
;   Production Value: Off

; error_reporting
;   Default Value: E_ALL & ~E_NOTICE
;   Development Value: E_ALL | E_STRICT
;   Production Value: E_ALL & ~E_DEPRECATED

; html_errors
;   Default Value: On
;   Development Value: On
;   Production value: Off

; log_errors
;   Default Value: Off
;   Development Value: On
;   Production Value: On

; magic_quotes_gpc
;   Default Value: On
;   Development Value: Off
;   Production Value: Off

; max_input_time
;   Default Value: -1 (Unlimited)
;   Development Value: 60 (60 seconds)
;   Production Value: 60 (60 seconds)

; output_buffering
;   Default Value: Off
;   Development Value: 4096
;   Production Value: 4096

; register_argc_argv
;   Default Value: On
;   Development Value: Off
;   Production Value: Off

; register_long_arrays
;   Default Value: On
;   Development Value: Off
;   Production Value: Off

; request_order
;   Default Value: None
;   Development Value: "GP"
;   Production Value: "GP"

; session.bug_compat_42
;   Default Value: On
;   Development Value: On
;   Production Value: Off

; session.bug_compat_warn
;   Default Value: On
;   Development Value: On
;   Production Value: Off

; session.gc_divisor
;   Default Value: 100
;   Development Value: 1000
;   Production Value: 1000

; session.hash_bits_per_character
;   Default Value: 4
;   Development Value: 5
;   Production Value: 5

; short_open_tag
;   Default Value: On
;   Development Value: Off
;   Production Value: Off

; track_errors
;   Default Value: Off
;   Development Value: On
;   Production Value: Off

; url_rewriter.tags
;   Default Value: "a=href,area=href,frame=src,form=,fieldset="
;   Development Value: "a=href,area=href,frame=src,input=src,form=fakeentry"
;   Production Value: "a=href,area=href,frame=src,input=src,form=fakeentry"

; variables_order
;   Default Value: "EGPCS"
;   Development Value: "GPCS"
;   Production Value: "GPCS"

;;;;;;;;;;;;;;;;;;;;
; php.ini Options  ;
;;;;;;;;;;;;;;;;;;;;
; Name for user-defined php.ini (.htaccess) files. Default is ".user.ini"
;user_ini.filename = ".user.ini"

; To disable this feature set this option to empty value
;user_ini.filename =

; TTL for user-defined php.ini files (time-to-live) in seconds. Default is 300 seconds (5 minutes)
;user_ini.cache_ttl = 300

;;;;;;;;;;;;;;;;;;;;
; Language Options ;
;;;;;;;;;;;;;;;;;;;;

; Enable the PHP scripting language engine under Apache.
; http://php.net/engine
engine = On

; This directive determines whether or not PHP will recognize code between
; <? and ?> tags as PHP source which should be processed as such. It's been
; recommended for several years that you not use the short tag "short cut" and
; instead to use the full <?php and ?> tag combination. With the wide spread use
; of XML and use of these tags by other languages, the server can become easily
; confused and end up parsing the wrong code in the wrong context. But because
; this short cut has been a feature for such a long time, it's currently still
; supported for backwards compatibility, but we recommend you don't use them.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/short-open-tag
short_open_tag = On

; Allow ASP-style <% %> tags.
; http://php.net/asp-tags
asp_tags = Off

; The number of significant digits displayed in floating point numbers.
; http://php.net/precision
precision = 14

; Enforce year 2000 compliance (will cause problems with non-compliant browsers)
; http://php.net/y2k-compliance
y2k_compliance = On

; Output buffering is a mechanism for controlling how much output data
; (excluding headers and cookies) PHP should keep internally before pushing that
; data to the client. If your application's output exceeds this setting, PHP
; will send that data in chunks of roughly the size you specify.
; Turning on this setting and managing its maximum buffer size can yield some
; interesting side-effects depending on your application and web server.
; You may be able to send headers and cookies after you've already sent output
; through print or echo. You also may see performance benefits if your server is
; emitting less packets due to buffered output versus PHP streaming the output
; as it gets it. On production servers, 4096 bytes is a good setting for performance
; reasons.
; Note: Output buffering can also be controlled via Output Buffering Control
;   functions.
; Possible Values:
;   On = Enabled and buffer is unlimited. (Use with caution)
;   Off = Disabled
;   Integer = Enables the buffer and sets its maximum size in bytes.
; Note: This directive is hardcoded to Off for the CLI SAPI
; Default Value: Off
; Development Value: 4096
; Production Value: 4096
; http://php.net/output-buffering
output_buffering = 4096

; You can redirect all of the output of your scripts to a function.  For
; example, if you set output_handler to "mb_output_handler", character
; encoding will be transparently converted to the specified encoding.
; Setting any output handler automatically turns on output buffering.
; Note: People who wrote portable scripts should not depend on this ini
;   directive. Instead, explicitly set the output handler using ob_start().
;   Using this ini directive may cause problems unless you know what script
;   is doing.
; Note: You cannot use both "mb_output_handler" with "ob_iconv_handler"
;   and you cannot use both "ob_gzhandler" and "zlib.output_compression".
; Note: output_handler must be empty if this is set 'On' !!!!
;   Instead you must use zlib.output_handler.
; http://php.net/output-handler
;output_handler =

; Transparent output compression using the zlib library
; Valid values for this option are 'off', 'on', or a specific buffer size
; to be used for compression (default is 4KB)
; Note: Resulting chunk size may vary due to nature of compression. PHP
;   outputs chunks that are few hundreds bytes each as a result of
;   compression. If you prefer a larger chunk size for better
;   performance, enable output_buffering in addition.
; Note: You need to use zlib.output_handler instead of the standard
;   output_handler, or otherwise the output will be corrupted.
; http://php.net/zlib.output-compression
zlib.output_compression = Off

; http://php.net/zlib.output-compression-level
;zlib.output_compression_level = -1

; You cannot specify additional output handlers if zlib.output_compression
; is activated here. This setting does the same as output_handler but in
; a different order.
; http://php.net/zlib.output-handler
;zlib.output_handler =

; Implicit flush tells PHP to tell the output layer to flush itself
; automatically after every output block.  This is equivalent to calling the
; PHP function flush() after each and every call to print() or echo() and each
; and every HTML block.  Turning this option on has serious performance
; implications and is generally recommended for debugging purposes only.
; http://php.net/implicit-flush
; Note: This directive is hardcoded to On for the CLI SAPI
implicit_flush = Off

; The unserialize callback function will be called (with the undefined class'
; name as parameter), if the unserializer finds an undefined class
; which should be instantiated. A warning appears if the specified function is
; not defined, or if the function doesn't include/implement the missing class.
; So only set this entry, if you really want to implement such a
; callback-function.
unserialize_callback_func =

; When floats & doubles are serialized store serialize_precision significant
; digits after the floating point. The default value ensures that when floats
; are decoded with unserialize, the data will remain the same.
serialize_precision = 100

; This directive allows you to enable and disable warnings which PHP will issue
; if you pass a value by reference at function call time. Passing values by
; reference at function call time is a deprecated feature which will be removed
; from PHP at some point in the near future. The acceptable method for passing a
; value by reference to a function is by declaring the reference in the functions
; definition, not at call time. This directive does not disable this feature, it
; only determines whether PHP will warn you about it or not. These warnings
; should enabled in development environments only.
; Default Value: On (Suppress warnings)
; Development Value: Off (Issue warnings)
; Production Value: Off (Issue warnings)
; http://php.net/allow-call-time-pass-reference
allow_call_time_pass_reference = Off

; Safe Mode
; http://php.net/safe-mode
safe_mode = Off

; By default, Safe Mode does a UID compare check when
; opening files. If you want to relax this to a GID compare,
; then turn on safe_mode_gid.
; http://php.net/safe-mode-gid
safe_mode_gid = Off

; When safe_mode is on, UID/GID checks are bypassed when
; including files from this directory and its subdirectories.
; (directory must also be in include_path or full path must
; be used when including)
; http://php.net/safe-mode-include-dir
safe_mode_include_dir =

; When safe_mode is on, only executables located in the safe_mode_exec_dir
; will be allowed to be executed via the exec family of functions.
; http://php.net/safe-mode-exec-dir
safe_mode_exec_dir =

; Setting certain environment variables may be a potential security breach.
; This directive contains a comma-delimited list of prefixes.  In Safe Mode,
; the user may only alter environment variables whose names begin with the
; prefixes supplied here.  By default, users will only be able to set
; environment variables that begin with PHP_ (e.g. PHP_FOO=BAR).
; Note:  If this directive is empty, PHP will let the user modify ANY
;   environment variable!
; http://php.net/safe-mode-allowed-env-vars
safe_mode_allowed_env_vars = PHP_

; This directive contains a comma-delimited list of environment variables that
; the end user won't be able to change using putenv().  These variables will be
; protected even if safe_mode_allowed_env_vars is set to allow to change them.
; http://php.net/safe-mode-protected-env-vars
safe_mode_protected_env_vars = LD_LIBRARY_PATH

; open_basedir, if set, limits all file operations to the defined directory
; and below.  This directive makes most sense if used in a per-directory
; or per-virtualhost web server configuration file. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
; http://php.net/open-basedir
;open_basedir =

; This directive allows you to disable certain functions for security reasons.
; It receives a comma-delimited list of function names. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
; http://php.net/disable-functions
disable_functions =

; This directive allows you to disable certain classes for security reasons.
; It receives a comma-delimited list of class names. This directive is
; *NOT* affected by whether Safe Mode is turned On or Off.
; http://php.net/disable-classes
disable_classes =

; Colors for Syntax Highlighting mode.  Anything that's acceptable in
; <span style="color: ???????"> would work.
; http://php.net/syntax-highlighting
;highlight.string  = #DD0000
;highlight.comment = #FF9900
;highlight.keyword = #007700
;highlight.bg      = #FFFFFF
;highlight.default = #0000BB
;highlight.html    = #000000

; If enabled, the request will be allowed to complete even if the user aborts
; the request. Consider enabling it if executing long requests, which may end up
; being interrupted by the user or a browser timing out. PHP's default behavior
; is to disable this feature.
; http://php.net/ignore-user-abort
;ignore_user_abort = On

; Determines the size of the realpath cache to be used by PHP. This value should
; be increased on systems where PHP opens many files to reflect the quantity of
; the file operations performed.
; http://php.net/realpath-cache-size
;realpath_cache_size = 16k

; Duration of time, in seconds for which to cache realpath information for a given
; file or directory. For systems with rarely changing files, consider increasing this
; value.
; http://php.net/realpath-cache-ttl
;realpath_cache_ttl = 120

;;;;;;;;;;;;;;;;;
; Miscellaneous ;
;;;;;;;;;;;;;;;;;

; Decides whether PHP may expose the fact that it is installed on the server
; (e.g. by adding its signature to the Web server header).  It is no security
; threat in any way, but it makes it possible to determine whether you use PHP
; on your server or not.
; http://php.net/expose-php
expose_php = On

;;;;;;;;;;;;;;;;;;;
; Resource Limits ;
;;;;;;;;;;;;;;;;;;;

; Maximum execution time of each script, in seconds
; http://php.net/max-execution-time
; Note: This directive is hardcoded to 0 for the CLI SAPI
max_execution_time = 30

; Maximum amount of time each script may spend parsing request data. It's a good
; idea to limit this time on productions servers in order to eliminate unexpectedly
; long running scripts.
; Note: This directive is hardcoded to -1 for the CLI SAPI
; Default Value: -1 (Unlimited)
; Development Value: 60 (60 seconds)
; Production Value: 60 (60 seconds)
; http://php.net/max-input-time
max_input_time = 60

; Maximum input variable nesting level
; http://php.net/max-input-nesting-level
;max_input_nesting_level = 64

; Maximum amount of memory a script may consume (128MB)
; http://php.net/memory-limit
memory_limit = 128M

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
; Error handling and logging ;
;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;

; This directive informs PHP of which errors, warnings and notices you would like
; it to take action for. The recommended way of setting values for this
; directive is through the use of the error level constants and bitwise
; operators. The error level constants are below here for convenience as well as
; some common settings and their meanings.
; By default, PHP is set to take action on all errors, notices and warnings EXCEPT
; those related to E_NOTICE and E_STRICT, which together cover best practices and
; recommended coding standards in PHP. For performance reasons, this is the
; recommend error reporting setting. Your production server shouldn't be wasting
; resources complaining about best practices and coding standards. That's what
; development servers and development settings are for.
; Note: The php.ini-development file has this setting as E_ALL | E_STRICT. This
; means it pretty much reports everything which is exactly what you want during
; development and early testing.
;
; Error Level Constants:
; E_ALL             - All errors and warnings (includes E_STRICT as of PHP 6.0.0)
; E_ERROR           - fatal run-time errors
; E_RECOVERABLE_ERROR  - almost fatal run-time errors
; E_WARNING         - run-time warnings (non-fatal errors)
; E_PARSE           - compile-time parse errors
; E_NOTICE          - run-time notices (these are warnings which often result
;                     from a bug in your code, but it's possible that it was
;                     intentional (e.g., using an uninitialized variable and
;                     relying on the fact it's automatically initialized to an
;                     empty string)
; E_STRICT          - run-time notices, enable to have PHP suggest changes
;                     to your code which will ensure the best interoperability
;                     and forward compatibility of your code
; E_CORE_ERROR      - fatal errors that occur during PHP's initial startup
; E_CORE_WARNING    - warnings (non-fatal errors) that occur during PHP's
;                     initial startup
; E_COMPILE_ERROR   - fatal compile-time errors
; E_COMPILE_WARNING - compile-time warnings (non-fatal errors)
; E_USER_ERROR      - user-generated error message
; E_USER_WARNING    - user-generated warning message
; E_USER_NOTICE     - user-generated notice message
; E_DEPRECATED      - warn about code that will not work in future versions
;                     of PHP
; E_USER_DEPRECATED - user-generated deprecation warnings
;
; Common Values:
;   E_ALL & ~E_NOTICE  (Show all errors, except for notices and coding standards warnings.)
;   E_ALL & ~E_NOTICE | E_STRICT  (Show all errors, except for notices)
;   E_COMPILE_ERROR|E_RECOVERABLE_ERROR|E_ERROR|E_CORE_ERROR  (Show only errors)
;   E_ALL | E_STRICT  (Show all errors, warnings and notices including coding standards.)
; Default Value: E_ALL & ~E_NOTICE
; Development Value: E_ALL | E_STRICT
; Production Value: E_ALL & ~E_DEPRECATED
; http://php.net/error-reporting
error_reporting = E_ALL & ~E_DEPRECATED

; This directive controls whether or not and where PHP will output errors,
; notices and warnings too. Error output is very useful during development, but
; it could be very dangerous in production environments. Depending on the code
; which is triggering the error, sensitive information could potentially leak
; out of your application such as database usernames and passwords or worse.
; It's recommended that errors be logged on production servers rather than
; having the errors sent to STDOUT.
; Possible Values:
;   Off = Do not display any errors
;   stderr = Display errors to STDERR (affects only CGI/CLI binaries!)
;   On or stdout = Display errors to STDOUT
; Default Value: On
; Development Value: On
; Production Value: Off
; http://php.net/display-errors
display_errors = Off

; The display of errors which occur during PHP's startup sequence are handled
; separately from display_errors. PHP's default behavior is to suppress those
; errors from clients. Turning the display of startup errors on can be useful in
; debugging configuration problems. But, it's strongly recommended that you
; leave this setting off on production servers.
; Default Value: Off
; Development Value: On
; Production Value: Off
; http://php.net/display-startup-errors
display_startup_errors = Off

; Besides displaying errors, PHP can also log errors to locations such as a
; server-specific log, STDERR, or a location specified by the error_log
; directive found below. While errors should not be displayed on productions
; servers they should still be monitored and logging is a great way to do that.
; Default Value: Off
; Development Value: On
; Production Value: On
; http://php.net/log-errors
log_errors = On

; Set maximum length of log_errors. In error_log information about the source is
; added. The default is 1024 and 0 allows to not apply any maximum length at all.
; http://php.net/log-errors-max-len
log_errors_max_len = 1024

; Do not log repeated messages. Repeated errors must occur in same file on same
; line unless ignore_repeated_source is set true.
; http://php.net/ignore-repeated-errors
ignore_repeated_errors = Off

; Ignore source of message when ignoring repeated messages. When this setting
; is On you will not log errors with repeated messages from different files or
; source lines.
; http://php.net/ignore-repeated-source
ignore_repeated_source = Off

; If this parameter is set to Off, then memory leaks will not be shown (on
; stdout or in the log). This has only effect in a debug compile, and if
; error reporting includes E_WARNING in the allowed list
; http://php.net/report-memleaks
report_memleaks = On

; This setting is on by default.
;report_zend_debug = 0

; Store the last error/warning message in $php_errormsg (boolean). Setting this value
; to On can assist in debugging and is appropriate for development servers. It should
; however be disabled on production servers.
; Default Value: Off
; Development Value: On
; Production Value: Off
; http://php.net/track-errors
track_errors = Off

; Turn off normal error reporting and emit XML-RPC error XML
; http://php.net/xmlrpc-errors
;xmlrpc_errors = 0

; An XML-RPC faultCode
;xmlrpc_error_number = 0

; When PHP displays or logs an error, it has the capability of inserting html
; links to documentation related to that error. This directive controls whether
; those HTML links appear in error messages or not. For performance and security
; reasons, it's recommended you disable this on production servers.
; Note: This directive is hardcoded to Off for the CLI SAPI
; Default Value: On
; Development Value: On
; Production value: Off
; http://php.net/html-errors
html_errors = Off

; If html_errors is set On PHP produces clickable error messages that direct
; to a page describing the error or function causing the error in detail.
; You can download a copy of the PHP manual from http://php.net/docs
; and change docref_root to the base URL of your local copy including the
; leading '/'. You must also specify the file extension being used including
; the dot. PHP's default behavior is to leave these settings empty.
; Note: Never use this feature for production boxes.
; http://php.net/docref-root
; Examples
;docref_root = "/phpmanual/"

; http://php.net/docref-ext
;docref_ext = .html

; String to output before an error message. PHP's default behavior is to leave
; this setting blank.
; http://php.net/error-prepend-string
; Example:
;error_prepend_string = "<font color=#ff0000>"

; String to output after an error message. PHP's default behavior is to leave
; this setting blank.
; http://php.net/error-append-string
; Example:
;error_append_string = "</font>"

; Log errors to specified file. PHP's default behavior is to leave this value
; empty.
; http://php.net/error-log
; Example:
;error_log = php_errors.log
; Log errors to syslog (Event Log on NT, not valid in Windows 95).
;error_log = syslog

;;;;;;;;;;;;;;;;;
; Data Handling ;
;;;;;;;;;;;;;;;;;

; The separator used in PHP generated URLs to separate arguments.
; PHP's default setting is "&".
; http://php.net/arg-separator.output
; Example:
;arg_separator.output = "&amp;"

; List of separator(s) used by PHP to parse input URLs into variables.
; PHP's default setting is "&".
; NOTE: Every character in this directive is considered as separator!
; http://php.net/arg-separator.input
; Example:
;arg_separator.input = ";&"

; This directive determines which super global arrays are registered when PHP
; starts up. If the register_globals directive is enabled, it also determines
; what order variables are populated into the global space. G,P,C,E & S are
; abbreviations for the following respective super globals: GET, POST, COOKIE,
; ENV and SERVER. There is a performance penalty paid for the registration of
; these arrays and because ENV is not as commonly used as the others, ENV is
; is not recommended on productions servers. You can still get access to
; the environment variables through getenv() should you need to.
; Default Value: "EGPCS"
; Development Value: "GPCS"
; Production Value: "GPCS";
; http://php.net/variables-order
variables_order = "GPCS"

; This directive determines which super global data (G,P,C,E & S) should
; be registered into the super global array REQUEST. If so, it also determines
; the order in which that data is registered. The values for this directive are
; specified in the same manner as the variables_order directive, EXCEPT one.
; Leaving this value empty will cause PHP to use the value set in the
; variables_order directive. It does not mean it will leave the super globals
; array REQUEST empty.
; Default Value: None
; Development Value: "GP"
; Production Value: "GP"
; http://php.net/request-order
request_order = "GP"

; Whether or not to register the EGPCS variables as global variables.  You may
; want to turn this off if you don't want to clutter your scripts' global scope
; with user data.
; You should do your best to write your scripts so that they do not require
; register_globals to be on;  Using form variables as globals can easily lead
; to possible security problems, if the code is not very well thought of.
; http://php.net/register-globals
register_globals = Off

; Determines whether the deprecated long $HTTP_*_VARS type predefined variables
; are registered by PHP or not. As they are deprecated, we obviously don't
; recommend you use them. They are on by default for compatibility reasons but
; they are not recommended on production servers.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/register-long-arrays
register_long_arrays = Off

; This directive determines whether PHP registers $argv & $argc each time it
; runs. $argv contains an array of all the arguments passed to PHP when a script
; is invoked. $argc contains an integer representing the number of arguments
; that were passed when the script was invoked. These arrays are extremely
; useful when running scripts from the command line. When this directive is
; enabled, registering these variables consumes CPU cycles and memory each time
; a script is executed. For performance reasons, this feature should be disabled
; on production servers.
; Note: This directive is hardcoded to On for the CLI SAPI
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/register-argc-argv
register_argc_argv = Off

; When enabled, the SERVER and ENV variables are created when they're first
; used (Just In Time) instead of when the script starts. If these variables
; are not used within a script, having this directive on will result in a
; performance gain. The PHP directives register_globals, register_long_arrays,
; and register_argc_argv must be disabled for this directive to have any affect.
; http://php.net/auto-globals-jit
auto_globals_jit = On

; Maximum size of POST data that PHP will accept.
; http://php.net/post-max-size
post_max_size = 8M

; Magic quotes are a preprocessing feature of PHP where PHP will attempt to
; escape any character sequences in GET, POST, COOKIE and ENV data which might
; otherwise corrupt data being placed in resources such as databases before
; making that data available to you. Because of character encoding issues and
; non-standard SQL implementations across many databases, it's not currently
; possible for this feature to be 100% accurate. PHP's default behavior is to
; enable the feature. We strongly recommend you use the escaping mechanisms
; designed specifically for the database your using instead of relying on this
; feature. Also note, this feature has been deprecated as of PHP 5.3.0 and is
; scheduled for removal in PHP 6.
; Default Value: On
; Development Value: Off
; Production Value: Off
; http://php.net/magic-quotes-gpc
magic_quotes_gpc = Off

; Magic quotes for runtime-generated data, e.g. data from SQL, from exec(), etc.
; http://php.net/magic-quotes-runtime
magic_quotes_runtime = Off

; Use Sybase-style magic quotes (escape ' with '' instead of \').
; http://php.net/magic-quotes-sybase
magic_quotes_sybase = Off

; Automatically add files before PHP document.
; http://php.net/auto-prepend-file
auto_prepend_file =

; Automatically add files after PHP document.
; http://php.net/auto-append-file
auto_append_file =

; By default, PHP will output a character encoding using
; the Content-type: header.  To disable sending of the charset, simply
; set it to be empty.
;
; PHP's built-in default is text/html
; http://php.net/default-mimetype
default_mimetype = "text/html"

; PHP's default character set is set to empty.
; http://php.net/default-charset
;default_charset = "iso-8859-1"

; Always populate the $HTTP_RAW_POST_DATA variable. PHP's default behavior is
; to disable this feature.
; http://php.net/always-populate-raw-post-data
;always_populate_raw_post_data = On

;;;;;;;;;;;;;;;;;;;;;;;;;
; Paths and Directories ;
;;;;;;;;;;;;;;;;;;;;;;;;;

; UNIX: "/path1:/path2"
;include_path = ".:/usr/share/php"
;
; Windows: "\path1;\path2"
;include_path = ".;c:\php\includes"
;
; PHP's default setting for include_path is ".;/path/to/php/pear"
; http://php.net/include-path

; The root of the PHP pages, used only if nonempty.
; if PHP was not compiled with FORCE_REDIRECT, you SHOULD set doc_root
; if you are running php as a CGI under any web server (other than IIS)
; see documentation for security issues.  The alternate is to use the
; cgi.force_redirect configuration below
; http://php.net/doc-root
doc_root =

; The directory under which PHP opens the script using /~username used only
; if nonempty.
; http://php.net/user-dir
user_dir =

; Directory in which the loadable extensions (modules) reside.
; http://php.net/extension-dir
; extension_dir = "./"
; On windows:
; extension_dir = "ext"

; Whether or not to enable the dl() function.  The dl() function does NOT work
; properly in multithreaded servers, such as IIS or Zeus, and is automatically
; disabled on them.
; http://php.net/enable-dl
enable_dl = Off

; cgi.force_redirect is necessary to provide security running PHP as a CGI under
; most web servers.  Left undefined, PHP turns this on by default.  You can
; turn it off here AT YOUR OWN RISK
; **You CAN safely turn this off for IIS, in fact, you MUST.**
; http://php.net/cgi.force-redirect
;cgi.force_redirect = 1

; if cgi.nph is enabled it will force cgi to always sent Status: 200 with
; every request. PHP's default behavior is to disable this feature.
;cgi.nph = 1

; if cgi.force_redirect is turned on, and you are not running under Apache or Netscape
; (iPlanet) web servers, you MAY need to set an environment variable name that PHP
; will look for to know it is OK to continue execution.  Setting this variable MAY
; cause security issues, KNOW WHAT YOU ARE DOING FIRST.
; http://php.net/cgi.redirect-status-env
;cgi.redirect_status_env = ;

; cgi.fix_pathinfo provides *real* PATH_INFO/PATH_TRANSLATED support for CGI.  PHP's
; previous behaviour was to set PATH_TRANSLATED to SCRIPT_FILENAME, and to not grok
; what PATH_INFO is.  For more information on PATH_INFO, see the cgi specs.  Setting
; this to 1 will cause PHP CGI to fix its paths to conform to the spec.  A setting
; of zero causes PHP to behave as before.  Default is 1.  You should fix your scripts
; to use SCRIPT_FILENAME rather than PATH_TRANSLATED.
; http://php.net/cgi.fix-pathinfo
;cgi.fix_pathinfo=1

; FastCGI under IIS (on WINNT based OS) supports the ability to impersonate
; security tokens of the calling client.  This allows IIS to define the
; security context that the request runs under.  mod_fastcgi under Apache
; does not currently support this feature (03/17/2002)
; Set to 1 if running under IIS.  Default is zero.
; http://php.net/fastcgi.impersonate
;fastcgi.impersonate = 1;

; Disable logging through FastCGI connection. PHP's default behavior is to enable
; this feature.
;fastcgi.logging = 0

; cgi.rfc2616_headers configuration option tells PHP what type of headers to
; use when sending HTTP response code. If it's set 0 PHP sends Status: header that
; is supported by Apache. When this option is set to 1 PHP will send
; RFC2616 compliant header.
; Default is zero.
; http://php.net/cgi.rfc2616-headers
;cgi.rfc2616_headers = 0

;;;;;;;;;;;;;;;;
; File Uploads ;
;;;;;;;;;;;;;;;;

; Whether to allow HTTP file uploads.
; http://php.net/file-uploads
file_uploads = On

; Temporary directory for HTTP uploaded files (will use system default if not
; specified).
; http://php.net/upload-tmp-dir
;upload_tmp_dir =

; Maximum allowed size for uploaded files.
; http://php.net/upload-max-filesize
upload_max_filesize = 2M

; Maximum number of files that can be uploaded via a single request
max_file_uploads = 20

;;;;;;;;;;;;;;;;;;
; Fopen wrappers ;
;;;;;;;;;;;;;;;;;;

; Whether to allow the treatment of URLs (like http:// or ftp://) as files.
; http://php.net/allow-url-fopen
allow_url_fopen = On

; Whether to allow include/require to open URLs (like http:// or ftp://) as files.
; http://php.net/allow-url-include
allow_url_include = Off

; Define the anonymous ftp password (your email address). PHP's default setting
; for this is empty.
; http://php.net/from
;from="john@doe.com"

; Define the User-Agent string. PHP's default setting for this is empty.
; http://php.net/user-agent
;user_agent="PHP"

; Default timeout for socket based streams (seconds)
; http://php.net/default-socket-timeout
default_socket_timeout = 60

; If your scripts have to deal with files from Macintosh systems,
; or you are running on a Mac and need to deal with files from
; unix or win32 systems, setting this flag will cause PHP to
; automatically detect the EOL character in those files so that
; fgets() and file() will work regardless of the source of the file.
; http://php.net/auto-detect-line-endings
;auto_detect_line_endings = Off

;;;;;;;;;;;;;;;;;;;;;;
; Dynamic Extensions ;
;;;;;;;;;;;;;;;;;;;;;;

; If you wish to have an extension loaded automatically, use the following
; syntax:
;
;   extension=modulename.extension
;
; For example, on Windows:
;
;   extension=msql.dll
;
; ... or under UNIX:
;
;   extension=msql.so
;
; ... or with a path:
;
;   extension=/path/to/extension/msql.so
;
; If you only provide the name of the extension, PHP will look for it in its
; default extension directory.
;

;;;;;;;;;;;;;;;;;;;
; Module Settings ;
;;;;;;;;;;;;;;;;;;;

[Date]
; Defines the default timezone used by the date functions
; http://php.net/date.timezone
;date.timezone =

; http://php.net/date.default-latitude
;date.default_latitude = 31.7667

; http://php.net/date.default-longitude
;date.default_longitude = 35.2333

; http://php.net/date.sunrise-zenith
;date.sunrise_zenith = 90.583333

; http://php.net/date.sunset-zenith
;date.sunset_zenith = 90.583333

[filter]
; http://php.net/filter.default
;filter.default = unsafe_raw

; http://php.net/filter.default-flags
;filter.default_flags =

[iconv]
;iconv.input_encoding = ISO-8859-1
;iconv.internal_encoding = ISO-8859-1
;iconv.output_encoding = ISO-8859-1

[intl]
;intl.default_locale =
; This directive allows you to produce PHP errors when some error
; happens within intl functions. The value is the level of the error produced.
; Default is 0, which does not produce any errors.
;intl.error_level = E_WARNING

[sqlite]
; http://php.net/sqlite.assoc-case
;sqlite.assoc_case = 0

[sqlite3]
;sqlite3.extension_dir =

[Pcre]
;PCRE library backtracking limit.
; http://php.net/pcre.backtrack-limit
;pcre.backtrack_limit=100000

;PCRE library recursion limit.
;Please note that if you set this value to a high number you may consume all
;the available process stack and eventually crash PHP (due to reaching the
;stack size limit imposed by the Operating System).
; http://php.net/pcre.recursion-limit
;pcre.recursion_limit=100000

[Pdo]
; Whether to pool ODBC connections. Can be one of "strict", "relaxed" or "off"
; http://php.net/pdo-odbc.connection-pooling
;pdo_odbc.connection_pooling=strict

;pdo_odbc.db2_instance_name

[Pdo_mysql]
; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/pdo_mysql.cache_size
pdo_mysql.cache_size = 2000

; Default socket name for local MySQL connects.  If empty, uses the built-in
; MySQL defaults.
; http://php.net/pdo_mysql.default-socket
pdo_mysql.default_socket=

[Phar]
; http://php.net/phar.readonly
;phar.readonly = On

; http://php.net/phar.require-hash
;phar.require_hash = On

;phar.cache_list =

[Syslog]
; Whether or not to define the various syslog variables (e.g. $LOG_PID,
; $LOG_CRON, etc.).  Turning it off is a good idea performance-wise.  In
; runtime, you can define these variables by calling define_syslog_variables().
; http://php.net/define-syslog-variables
define_syslog_variables  = Off

[mail function]
; For Win32 only.
; http://php.net/smtp
SMTP = localhost
; http://php.net/smtp-port
smtp_port = 25

; For Win32 only.
; http://php.net/sendmail-from
;sendmail_from = me@example.com

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; http://php.net/sendmail-path
;sendmail_path =

; Force the addition of the specified parameters to be passed as extra parameters
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =

; Add X-PHP-Originating-Script: that will include uid of the script followed by the filename
mail.add_x_header = On

; Log all mail() calls including the full path of the script, line #, to address and headers
;mail.log =

[SQL]
; http://php.net/sql.safe-mode
sql.safe_mode = Off

[ODBC]
; http://php.net/odbc.default-db
;odbc.default_db    =  Not yet implemented

; http://php.net/odbc.default-user
;odbc.default_user  =  Not yet implemented

; http://php.net/odbc.default-pw
;odbc.default_pw    =  Not yet implemented

; Controls the ODBC cursor model.
; Default: SQL_CURSOR_STATIC (default).
;odbc.default_cursortype

; Allow or prevent persistent links.
; http://php.net/odbc.allow-persistent
odbc.allow_persistent = On

; Check that a connection is still valid before reuse.
; http://php.net/odbc.check-persistent
odbc.check_persistent = On

; Maximum number of persistent links.  -1 means no limit.
; http://php.net/odbc.max-persistent
odbc.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
; http://php.net/odbc.max-links
odbc.max_links = -1

; Handling of LONG fields.  Returns number of bytes to variables.  0 means
; passthru.
; http://php.net/odbc.defaultlrl
odbc.defaultlrl = 4096

; Handling of binary data.  0 means passthru, 1 return as is, 2 convert to char.
; See the documentation on odbc_binmode and odbc_longreadlen for an explanation
; of odbc.defaultlrl and odbc.defaultbinmode
; http://php.net/odbc.defaultbinmode
odbc.defaultbinmode = 1

;birdstep.max_links = -1

[Interbase]
; Allow or prevent persistent links.
ibase.allow_persistent = 1

; Maximum number of persistent links.  -1 means no limit.
ibase.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
ibase.max_links = -1

; Default database name for ibase_connect().
;ibase.default_db =

; Default username for ibase_connect().
;ibase.default_user =

; Default password for ibase_connect().
;ibase.default_password =

; Default charset for ibase_connect().
;ibase.default_charset =

; Default timestamp format.
ibase.timestampformat = "%Y-%m-%d %H:%M:%S"

; Default date format.
ibase.dateformat = "%Y-%m-%d"

; Default time format.
ibase.timeformat = "%H:%M:%S"

[MySQL]
; Allow accessing, from PHP's perspective, local files with LOAD DATA statements
; http://php.net/mysql.allow_local_infile
mysql.allow_local_infile = On

; Allow or prevent persistent links.
; http://php.net/mysql.allow-persistent
mysql.allow_persistent = On

; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/mysql.cache_size
mysql.cache_size = 2000

; Maximum number of persistent links.  -1 means no limit.
; http://php.net/mysql.max-persistent
mysql.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
; http://php.net/mysql.max-links
mysql.max_links = -1

; Default port number for mysql_connect().  If unset, mysql_connect() will use
; the $MYSQL_TCP_PORT or the mysql-tcp entry in /etc/services or the
; compile-time value defined MYSQL_PORT (in that order).  Win32 will only look
; at MYSQL_PORT.
; http://php.net/mysql.default-port
mysql.default_port =

; Default socket name for local MySQL connects.  If empty, uses the built-in
; MySQL defaults.
; http://php.net/mysql.default-socket
mysql.default_socket =

; Default host for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysql.default-host
mysql.default_host =

; Default user for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysql.default-user
mysql.default_user =

; Default password for mysql_connect() (doesn't apply in safe mode).
; Note that this is generally a *bad* idea to store passwords in this file.
; *Any* user with PHP access can run 'echo get_cfg_var("mysql.default_password")
; and reveal this password!  And of course, any users with read access to this
; file will be able to reveal the password as well.
; http://php.net/mysql.default-password
mysql.default_password =

; Maximum time (in seconds) for connect timeout. -1 means no limit
; http://php.net/mysql.connect-timeout
mysql.connect_timeout = 60

; Trace mode. When trace_mode is active (=On), warnings for table/index scans and
; SQL-Errors will be displayed.
; http://php.net/mysql.trace-mode
mysql.trace_mode = Off

[MySQLi]

; Maximum number of persistent links.  -1 means no limit.
; http://php.net/mysqli.max-persistent
mysqli.max_persistent = -1

; Allow accessing, from PHP's perspective, local files with LOAD DATA statements
; http://php.net/mysqli.allow_local_infile
;mysqli.allow_local_infile = On

; Allow or prevent persistent links.
; http://php.net/mysqli.allow-persistent
mysqli.allow_persistent = On

; Maximum number of links.  -1 means no limit.
; http://php.net/mysqli.max-links
mysqli.max_links = -1

; If mysqlnd is used: Number of cache slots for the internal result set cache
; http://php.net/mysqli.cache_size
mysqli.cache_size = 2000

; Default port number for mysqli_connect().  If unset, mysqli_connect() will use
; the $MYSQL_TCP_PORT or the mysql-tcp entry in /etc/services or the
; compile-time value defined MYSQL_PORT (in that order).  Win32 will only look
; at MYSQL_PORT.
; http://php.net/mysqli.default-port
mysqli.default_port = 3306

; Default socket name for local MySQL connects.  If empty, uses the built-in
; MySQL defaults.
; http://php.net/mysqli.default-socket
mysqli.default_socket =

; Default host for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysqli.default-host
mysqli.default_host =

; Default user for mysql_connect() (doesn't apply in safe mode).
; http://php.net/mysqli.default-user
mysqli.default_user =

; Default password for mysqli_connect() (doesn't apply in safe mode).
; Note that this is generally a *bad* idea to store passwords in this file.
; *Any* user with PHP access can run 'echo get_cfg_var("mysqli.default_pw")
; and reveal this password!  And of course, any users with read access to this
; file will be able to reveal the password as well.
; http://php.net/mysqli.default-pw
mysqli.default_pw =

; Allow or prevent reconnect
mysqli.reconnect = Off

[mysqlnd]
; Enable / Disable collection of general statstics by mysqlnd which can be
; used to tune and monitor MySQL operations.
; http://php.net/mysqlnd.collect_statistics
mysqlnd.collect_statistics = On

; Enable / Disable collection of memory usage statstics by mysqlnd which can be
; used to tune and monitor MySQL operations.
; http://php.net/mysqlnd.collect_memory_statistics
mysqlnd.collect_memory_statistics = Off

; Size of a pre-allocated buffer used when sending commands to MySQL in bytes.
; http://php.net/mysqlnd.net_cmd_buffer_size
;mysqlnd.net_cmd_buffer_size = 2048

; Size of a pre-allocated buffer used for reading data sent by the server in
; bytes.
; http://php.net/mysqlnd.net_read_buffer_size
;mysqlnd.net_read_buffer_size = 32768

[OCI8]

; Connection: Enables privileged connections using external
; credentials (OCI_SYSOPER, OCI_SYSDBA)
; http://php.net/oci8.privileged-connect
;oci8.privileged_connect = Off

; Connection: The maximum number of persistent OCI8 connections per
; process. Using -1 means no limit.
; http://php.net/oci8.max-persistent
;oci8.max_persistent = -1

; Connection: The maximum number of seconds a process is allowed to
; maintain an idle persistent connection. Using -1 means idle
; persistent connections will be maintained forever.
; http://php.net/oci8.persistent-timeout
;oci8.persistent_timeout = -1

; Connection: The number of seconds that must pass before issuing a
; ping during oci_pconnect() to check the connection validity. When
; set to 0, each oci_pconnect() will cause a ping. Using -1 disables
; pings completely.
; http://php.net/oci8.ping-interval
;oci8.ping_interval = 60

; Connection: Set this to a user chosen connection class to be used
; for all pooled server requests with Oracle 11g Database Resident
; Connection Pooling (DRCP).  To use DRCP, this value should be set to
; the same string for all web servers running the same application,
; the database pool must be configured, and the connection string must
; specify to use a pooled server.
;oci8.connection_class =

; High Availability: Using On lets PHP receive Fast Application
; Notification (FAN) events generated when a database node fails. The
; database must also be configured to post FAN events.
;oci8.events = Off

; Tuning: This option enables statement caching, and specifies how
; many statements to cache. Using 0 disables statement caching.
; http://php.net/oci8.statement-cache-size
;oci8.statement_cache_size = 20

; Tuning: Enables statement prefetching and sets the default number of
; rows that will be fetched automatically after statement execution.
; http://php.net/oci8.default-prefetch
;oci8.default_prefetch = 100

; Compatibility. Using On means oci_close() will not close
; oci_connect() and oci_new_connect() connections.
; http://php.net/oci8.old-oci-close-semantics
;oci8.old_oci_close_semantics = Off

[PostgresSQL]
; Allow or prevent persistent links.
; http://php.net/pgsql.allow-persistent
pgsql.allow_persistent = On

; Detect broken persistent links always with pg_pconnect().
; Auto reset feature requires a little overheads.
; http://php.net/pgsql.auto-reset-persistent
pgsql.auto_reset_persistent = Off

; Maximum number of persistent links.  -1 means no limit.
; http://php.net/pgsql.max-persistent
pgsql.max_persistent = -1

; Maximum number of links (persistent+non persistent).  -1 means no limit.
; http://php.net/pgsql.max-links
pgsql.max_links = -1

; Ignore PostgreSQL backends Notice message or not.
; Notice message logging require a little overheads.
; http://php.net/pgsql.ignore-notice
pgsql.ignore_notice = 0

; Log PostgreSQL backends Noitce message or not.
; Unless pgsql.ignore_notice=0, module cannot log notice message.
; http://php.net/pgsql.log-notice
pgsql.log_notice = 0

[Sybase-CT]
; Allow or prevent persistent links.
; http://php.net/sybct.allow-persistent
sybct.allow_persistent = On

; Maximum number of persistent links.  -1 means no limit.
; http://php.net/sybct.max-persistent
sybct.max_persistent = -1

; Maximum number of links (persistent + non-persistent).  -1 means no limit.
; http://php.net/sybct.max-links
sybct.max_links = -1

; Minimum server message severity to display.
; http://php.net/sybct.min-server-severity
sybct.min_server_severity = 10

; Minimum client message severity to display.
; http://php.net/sybct.min-client-severity
sybct.min_client_severity = 10

; Set per-context timeout
; http://php.net/sybct.timeout
;sybct.timeout=

;sybct.packet_size

; The maximum time in seconds to wait for a connection attempt to succeed before returning failure.
; Default: one minute
;sybct.login_timeout=

; The name of the host you claim to be connecting from, for display by sp_who.
; Default: none
;sybct.hostname=

; Allows you to define how often deadlocks are to be retried. -1 means "forever".
; Default: 0
;sybct.deadlock_retry_count=

[bcmath]
; Number of decimal digits for all bcmath functions.
; http://php.net/bcmath.scale
bcmath.scale = 0

[browscap]
; http://php.net/browscap
;browscap = extra/browscap.ini

[Session]
; Handler used to store/retrieve data.
; http://php.net/session.save-handler
session.save_handler = files

; Argument passed to save_handler.  In the case of files, this is the path
; where data files are stored. Note: Windows users have to change this
; variable in order to use PHP's session functions.
;
; The path can be defined as:
;
;     session.save_path = "N;/path"
;
; where N is an integer.  Instead of storing all the session files in
; /path, what this will do is use subdirectories N-levels deep, and
; store the session data in those directories.  This is useful if you
; or your OS have problems with lots of files in one directory, and is
; a more efficient layout for servers that handle lots of sessions.
;
; NOTE 1: PHP will not create this directory structure automatically.
;         You can use the script in the ext/session dir for that purpose.
; NOTE 2: See the section on garbage collection below if you choose to
;         use subdirectories for session storage
;
; The file storage module creates files using mode 600 by default.
; You can change that by using
;
;     session.save_path = "N;MODE;/path"
;
; where MODE is the octal representation of the mode. Note that this
; does not overwrite the process's umask.
; http://php.net/session.save-path
;session.save_path = "/tmp"

; Whether to use cookies.
; http://php.net/session.use-cookies
session.use_cookies = 1

; http://php.net/session.cookie-secure
;session.cookie_secure =

; This option forces PHP to fetch and use a cookie for storing and maintaining
; the session id. We encourage this operation as it's very helpful in combatting
; session hijacking when not specifying and managing your own session id. It is
; not the end all be all of session hijacking defense, but it's a good start.
; http://php.net/session.use-only-cookies
session.use_only_cookies = 1

; Name of the session (used as cookie name).
; http://php.net/session.name
session.name = PHPSESSID

; Initialize session on request startup.
; http://php.net/session.auto-start
session.auto_start = 0

; Lifetime in seconds of cookie or, if 0, until browser is restarted.
; http://php.net/session.cookie-lifetime
session.cookie_lifetime = 0

; The path for which the cookie is valid.
; http://php.net/session.cookie-path
session.cookie_path = /

; The domain for which the cookie is valid.
; http://php.net/session.cookie-domain
session.cookie_domain =

; Whether or not to add the httpOnly flag to the cookie, which makes it inaccessible to browser scripting languages such as JavaScript.
; http://php.net/session.cookie-httponly
session.cookie_httponly =

; Handler used to serialize data.  php is the standard serializer of PHP.
; http://php.net/session.serialize-handler
session.serialize_handler = php

; Defines the probability that the 'garbage collection' process is started
; on every session initialization. The probability is calculated by using
; gc_probability/gc_divisor. Where session.gc_probability is the numerator
; and gc_divisor is the denominator in the equation. Setting this value to 1
; when the session.gc_divisor value is 100 will give you approximately a 1% chance
; the gc will run on any give request.
; Default Value: 1
; Development Value: 1
; Production Value: 1
; http://php.net/session.gc-probability
session.gc_probability = 1

; Defines the probability that the 'garbage collection' process is started on every
; session initialization. The probability is calculated by using the following equation:
; gc_probability/gc_divisor. Where session.gc_probability is the numerator and
; session.gc_divisor is the denominator in the equation. Setting this value to 1
; when the session.gc_divisor value is 100 will give you approximately a 1% chance
; the gc will run on any give request. Increasing this value to 1000 will give you
; a 0.1% chance the gc will run on any give request. For high volume production servers,
; this is a more efficient approach.
; Default Value: 100
; Development Value: 1000
; Production Value: 1000
; http://php.net/session.gc-divisor
session.gc_divisor = 1000

; After this number of seconds, stored data will be seen as 'garbage' and
; cleaned up by the garbage collection process.
; http://php.net/session.gc-maxlifetime
session.gc_maxlifetime = 1440

; NOTE: If you are using the subdirectory option for storing session files
;       (see session.save_path above), then garbage collection does *not*
;       happen automatically.  You will need to do your own garbage
;       collection through a shell script, cron entry, or some other method.
;       For example, the following script would is the equivalent of
;       setting session.gc_maxlifetime to 1440 (1440 seconds = 24 minutes):
;          cd /path/to/sessions; find -cmin +24 | xargs rm

; PHP 4.2 and less have an undocumented feature/bug that allows you to
; to initialize a session variable in the global scope, even when register_globals
; is disabled.  PHP 4.3 and later will warn you, if this feature is used.
; You can disable the feature and the warning separately. At this time,
; the warning is only displayed, if bug_compat_42 is enabled. This feature
; introduces some serious security problems if not handled correctly. It's
; recommended that you do not use this feature on production servers. But you
; should enable this on development servers and enable the warning as well. If you
; do not enable the feature on development servers, you won't be warned when it's
; used and debugging errors caused by this can be difficult to track down.
; Default Value: On
; Development Value: On
; Production Value: Off
; http://php.net/session.bug-compat-42
session.bug_compat_42 = Off

; This setting controls whether or not you are warned by PHP when initializing a
; session value into the global space. session.bug_compat_42 must be enabled before
; these warnings can be issued by PHP. See the directive above for more information.
; Default Value: On
; Development Value: On
; Production Value: Off
; http://php.net/session.bug-compat-warn
session.bug_compat_warn = Off

; Check HTTP Referer to invalidate externally stored URLs containing ids.
; HTTP_REFERER has to contain this substring for the session to be
; considered as valid.
; http://php.net/session.referer-check
session.referer_check =

; How many bytes to read from the file.
; http://php.net/session.entropy-length
session.entropy_length = 0

; Specified here to create the session id.
; http://php.net/session.entropy-file
;session.entropy_file = /dev/urandom
session.entropy_file =

; http://php.net/session.entropy-length
;session.entropy_length = 16

; Set to {nocache,private,public,} to determine HTTP caching aspects
; or leave this empty to avoid sending anti-caching headers.
; http://php.net/session.cache-limiter
session.cache_limiter = nocache

; Document expires after n minutes.
; http://php.net/session.cache-expire
session.cache_expire = 180

; trans sid support is disabled by default.
; Use of trans sid may risk your users security.
; Use this option with caution.
; - User may send URL contains active session ID
;   to other person via. email/irc/etc.
; - URL that contains active session ID may be stored
;   in publically accessible computer.
; - User may access your site with the same session ID
;   always using URL stored in browser's history or bookmarks.
; http://php.net/session.use-trans-sid
session.use_trans_sid = 0

; Select a hash function for use in generating session ids.
; Possible Values
;   0  (MD5 128 bits)
;   1  (SHA-1 160 bits)
; This option may also be set to the name of any hash function supported by
; the hash extension. A list of available hashes is returned by the hash_alogs()
; function.
; http://php.net/session.hash-function
session.hash_function = 0

; Define how many bits are stored in each character when converting
; the binary hash data to something readable.
; Possible values:
;   4  (4 bits: 0-9, a-f)
;   5  (5 bits: 0-9, a-v)
;   6  (6 bits: 0-9, a-z, A-Z, "-", ",")
; Default Value: 4
; Development Value: 5
; Production Value: 5
; http://php.net/session.hash-bits-per-character
session.hash_bits_per_character = 5

; The URL rewriter will look for URLs in a defined set of HTML tags.
; form/fieldset are special; if you include them here, the rewriter will
; add a hidden <input> field with the info which is otherwise appended
; to URLs.  If you want XHTML conformity, remove the form entry.
; Note that all valid entries require a "=", even if no value follows.
; Default Value: "a=href,area=href,frame=src,form=,fieldset="
; Development Value: "a=href,area=href,frame=src,input=src,form=fakeentry"
; Production Value: "a=href,area=href,frame=src,input=src,form=fakeentry"
; http://php.net/url-rewriter.tags
url_rewriter.tags = "a=href,area=href,frame=src,input=src,form=fakeentry"

[MSSQL]
; Allow or prevent persistent links.
mssql.allow_persistent = On

; Maximum number of persistent links.  -1 means no limit.
mssql.max_persistent = -1

; Maximum number of links (persistent+non persistent).  -1 means no limit.
mssql.max_links = -1

; Minimum error severity to display.
mssql.min_error_severity = 10

; Minimum message severity to display.
mssql.min_message_severity = 10

; Compatibility mode with old versions of PHP 3.0.
mssql.compatability_mode = Off

; Connect timeout
;mssql.connect_timeout = 5

; Query timeout
;mssql.timeout = 60

; Valid range 0 - 2147483647.  Default = 4096.
;mssql.textlimit = 4096

; Valid range 0 - 2147483647.  Default = 4096.
;mssql.textsize = 4096

; Limits the number of records in each batch.  0 = all records in one batch.
;mssql.batchsize = 0

; Specify how datetime and datetim4 columns are returned
; On => Returns data converted to SQL server settings
; Off => Returns values as YYYY-MM-DD hh:mm:ss
;mssql.datetimeconvert = On

; Use NT authentication when connecting to the server
mssql.secure_connection = Off

; Specify max number of processes. -1 = library default
; msdlib defaults to 25
; FreeTDS defaults to 4096
;mssql.max_procs = -1

; Specify client character set.
; If empty or not set the client charset from freetds.comf is used
; This is only used when compiled with FreeTDS
;mssql.charset = "ISO-8859-1"

[Assertion]
; Assert(expr); active by default.
; http://php.net/assert.active
;assert.active = On

; Issue a PHP warning for each failed assertion.
; http://php.net/assert.warning
;assert.warning = On

; Don't bail out by default.
; http://php.net/assert.bail
;assert.bail = Off

; User-function to be called if an assertion fails.
; http://php.net/assert.callback
;assert.callback = 0

; Eval the expression with current error_reporting().  Set to true if you want
; error_reporting(0) around the eval().
; http://php.net/assert.quiet-eval
;assert.quiet_eval = 0

[COM]
; path to a file containing GUIDs, IIDs or filenames of files with TypeLibs
; http://php.net/com.typelib-file
;com.typelib_file =

; allow Distributed-COM calls
; http://php.net/com.allow-dcom
;com.allow_dcom = true

; autoregister constants of a components typlib on com_load()
; http://php.net/com.autoregister-typelib
;com.autoregister_typelib = true

; register constants casesensitive
; http://php.net/com.autoregister-casesensitive
;com.autoregister_casesensitive = false

; show warnings on duplicate constant registrations
; http://php.net/com.autoregister-verbose
;com.autoregister_verbose = true

; The default character set code-page to use when passing strings to and from COM objects.
; Default: system ANSI code page
;com.code_page=

[mbstring]
; language for internal character representation.
; http://php.net/mbstring.language
;mbstring.language = Japanese

; internal/script encoding.
; Some encoding cannot work as internal encoding.
; (e.g. SJIS, BIG5, ISO-2022-*)
; http://php.net/mbstring.internal-encoding
;mbstring.internal_encoding = EUC-JP

; http input encoding.
; http://php.net/mbstring.http-input
;mbstring.http_input = auto

; http output encoding. mb_output_handler must be
; registered as output buffer to function
; http://php.net/mbstring.http-output
;mbstring.http_output = SJIS

; enable automatic encoding translation according to
; mbstring.internal_encoding setting. Input chars are
; converted to internal encoding by setting this to On.
; Note: Do _not_ use automatic encoding translation for
;       portable libs/applications.
; http://php.net/mbstring.encoding-translation
;mbstring.encoding_translation = Off

; automatic encoding detection order.
; auto means
; http://php.net/mbstring.detect-order
;mbstring.detect_order = auto

; substitute_character used when character cannot be converted
; one from another
; http://php.net/mbstring.substitute-character
;mbstring.substitute_character = none;

; overload(replace) single byte functions by mbstring functions.
; mail(), ereg(), etc are overloaded by mb_send_mail(), mb_ereg(),
; etc. Possible values are 0,1,2,4 or combination of them.
; For example, 7 for overload everything.
; 0: No overload
; 1: Overload mail() function
; 2: Overload str*() functions
; 4: Overload ereg*() functions
; http://php.net/mbstring.func-overload
;mbstring.func_overload = 0

; enable strict encoding detection.
;mbstring.strict_detection = Off

; This directive specifies the regex pattern of content types for which mb_output_handler()
; is activated.
; Default: mbstring.http_output_conv_mimetype=^(text/|application/xhtml\+xml)
;mbstring.http_output_conv_mimetype=

; Allows to set script encoding. Only affects if PHP is compiled with --enable-zend-multibyte
; Default: ""
;mbstring.script_encoding=

[gd]
; Tell the jpeg decode to ignore warnings and try to create
; a gd image. The warning will then be displayed as notices
; disabled by default
; http://php.net/gd.jpeg-ignore-warning
;gd.jpeg_ignore_warning = 0

[exif]
; Exif UNICODE user comments are handled as UCS-2BE/UCS-2LE and JIS as JIS.
; With mbstring support this will automatically be converted into the encoding
; given by corresponding encode setting. When empty mbstring.internal_encoding
; is used. For the decode settings you can distinguish between motorola and
; intel byte order. A decode setting cannot be empty.
; http://php.net/exif.encode-unicode
;exif.encode_unicode = ISO-8859-15

; http://php.net/exif.decode-unicode-motorola
;exif.decode_unicode_motorola = UCS-2BE

; http://php.net/exif.decode-unicode-intel
;exif.decode_unicode_intel    = UCS-2LE

; http://php.net/exif.encode-jis
;exif.encode_jis =

; http://php.net/exif.decode-jis-motorola
;exif.decode_jis_motorola = JIS

; http://php.net/exif.decode-jis-intel
;exif.decode_jis_intel    = JIS

[Tidy]
; The path to a default tidy configuration file to use when using tidy
; http://php.net/tidy.default-config
;tidy.default_config = /usr/local/lib/php/default.tcfg

; Should tidy clean and repair output automatically?
; WARNING: Do not use this option if you are generating non-html content
; such as dynamic images
; http://php.net/tidy.clean-output
tidy.clean_output = Off

[soap]
; Enables or disables WSDL caching feature.
; http://php.net/soap.wsdl-cache-enabled
soap.wsdl_cache_enabled=1

; Sets the directory name where SOAP extension will put cache files.
; http://php.net/soap.wsdl-cache-dir
soap.wsdl_cache_dir="/tmp"

; (time to live) Sets the number of second while cached file will be used
; instead of original one.
; http://php.net/soap.wsdl-cache-ttl
soap.wsdl_cache_ttl=86400

; Sets the size of the cache limit. (Max. number of WSDL files to cache)
soap.wsdl_cache_limit = 5

[sysvshm]
; A default size of the shared memory segment
;sysvshm.init_mem = 10000

[ldap]
; Sets the maximum number of open links or -1 for unlimited.
ldap.max_links = -1

[mcrypt]
; For more information about mcrypt settings see http://php.net/mcrypt-module-open

; Directory where to load mcrypt algorithms
; Default: Compiled in into libmcrypt (usually /usr/local/lib/libmcrypt)
;mcrypt.algorithms_dir=

; Directory where to load mcrypt modes
; Default: Compiled in into libmcrypt (usually /usr/local/lib/libmcrypt)
;mcrypt.modes_dir=

[dba]
;dba.default_handler=

; Local Variables:
; tab-width: 4
; End:
```

Also, your apache.conf, again, here's mine:
```
#
# Based upon the NCSA server configuration files originally by Rob McCool.
#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See http://httpd.apache.org/docs/2.2/ for detailed information about
# the directives.
#
# Do NOT simply read the instructions in here without understanding
# what they do.  They're here only as hints or reminders.  If you are unsure
# consult the online docs. You have been warned.  
#
# The configuration directives are grouped into three basic sections:
#  1. Directives that control the operation of the Apache server process as a
#     whole (the 'global environment').
#  2. Directives that define the parameters of the 'main' or 'default' server,
#     which responds to requests that aren't handled by a virtual host.
#     These directives also provide default values for the settings
#     of all virtual hosts.
#  3. Settings for virtual hosts, which allow Web requests to be sent to
#     different IP addresses or hostnames and have them handled by the
#     same Apache server process.
#
# Configuration and logfile names: If the filenames you specify for many
# of the server's control files begin with "/" (or "drive:/" for Win32), the
# server will use that explicit path.  If the filenames do *not* begin
# with "/", the value of ServerRoot is prepended -- so "/var/log/apache2/foo.log"
# with ServerRoot set to "" will be interpreted by the
# server as "//var/log/apache2/foo.log".
#

### Section 1: Global Environment
#
# The directives in this section affect the overall operation of Apache,
# such as the number of concurrent requests it can handle or where it
# can find its configuration files.
#

#
# ServerRoot: The top of the directory tree under which the server's
# configuration, error, and log files are kept.
#
# NOTE!  If you intend to place this on an NFS (or otherwise network)
# mounted filesystem then please read the LockFile documentation (available
# at <URL:http://httpd.apache.org/docs-2.1/mod/mpm_common.html#lockfile>);
# you will save yourself a lot of trouble.
#
# Do NOT add a slash at the end of the directory path.
#
ServerRoot "/etc/apache2"

#
# The accept serialization lock file MUST BE STORED ON A LOCAL DISK.
#
#<IfModule !mpm_winnt.c>
#<IfModule !mpm_netware.c>
LockFile /var/lock/apache2/accept.lock
#</IfModule>
#</IfModule>

#
# PidFile: The file in which the server should record its process
# identification number when it starts.
# This needs to be set in /etc/apache2/envvars
#
PidFile ${APACHE_PID_FILE}

#
# Timeout: The number of seconds before receives and sends time out.
#
Timeout 300

#
# KeepAlive: Whether or not to allow persistent connections (more than
# one request per connection). Set to "Off" to deactivate.
#
KeepAlive On

#
# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.
#
MaxKeepAliveRequests 100

#
# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 15

##
## Server-Pool Size Regulation (MPM specific)
## 

# prefork MPM
# StartServers: number of server processes to start
# MinSpareServers: minimum number of server processes which are kept spare
# MaxSpareServers: maximum number of server processes which are kept spare
# MaxClients: maximum number of server processes allowed to start
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# worker MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

# event MPM
# StartServers: initial number of server processes to start
# MaxClients: maximum number of simultaneous client connections
# MinSpareThreads: minimum number of worker threads which are kept spare
# MaxSpareThreads: maximum number of worker threads which are kept spare
# ThreadsPerChild: constant number of worker threads in each server process
# MaxRequestsPerChild: maximum number of requests a server process serves
<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

# These need to be set in /etc/apache2/envvars
User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

#
# AccessFileName: The name of the file to look for in each directory
# for additional configuration directives.  See also the AllowOverride
# directive.
#

AccessFileName .htaccess

#
# The following lines prevent .htaccess and .htpasswd files from being 
# viewed by Web clients. 
#
<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

#
# DefaultType is the default MIME type the server will use for a document
# if it cannot otherwise determine one, such as from filename extensions.
# If your server contains mostly text or HTML documents, "text/plain" is
# a good value.  If most of your content is binary, such as applications
# or images, you may want to use "application/octet-stream" instead to
# keep browsers from trying to display binary files as though they are
# text.
#
DefaultType text/plain


#
# HostnameLookups: Log the names of clients or just their IP addresses
# e.g., www.apache.org (on) or 204.62.129.132 (off).
# The default is off because it'd be overall better for the net if people
# had to knowingly turn this feature on, since enabling it means that
# each client request will result in AT LEAST one lookup request to the
# nameserver.
#
HostnameLookups Off

# ErrorLog: The location of the error log file.
# If you do not specify an ErrorLog directive within a <VirtualHost>
# container, error messages relating to that virtual host will be
# logged here.  If you *do* define an error logfile for a <VirtualHost>
# container, that host's errors will be logged there and not here.
#
ErrorLog /var/log/apache2/error.log

#
# LogLevel: Control the number of messages logged to the error_log.
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
#
LogLevel warn

# Include module configuration:
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf

# Include all the user configurations:
Include /etc/apache2/httpd.conf

# Include ports listing
Include /etc/apache2/ports.conf

#
# The following directives define some format nicknames for use with
# a CustomLog directive (see below).
# If you are behind a reverse proxy, you might want to change %h into %{X-Forwarded-For}i
#
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent

#
# Define an access log for VirtualHosts that don't define their own logfile
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined


# Include of directories ignores editors' and dpkg's backup files,
# see README.Debian for details.

# Include generic snippets of statements
Include /etc/apache2/conf.d/

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

ServerName localhost
```

and your sites-available/default:
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by fopetesl on 2010-07-07
Just in case we differ on versions -
what versions of PHP, MySQL & Apache are you running?

Mine are:
un  php-pear           <none>             (no description available)
ii  php5               5.3.2-1ubuntu4.2   server-side, HTML-embedded scripting language (metap
ii  php5-cgi           5.3.2-1ubuntu4.2   server-side, HTML-embedded scripting language (CGI b
ii  php5-cli           5.3.2-1ubuntu4.2   command-line interpreter for the php5 scripting lang
ii  php5-common        5.3.2-1ubuntu4.2   Common files for packages built from the php5 source

[COLOR="Blue"]== there's more PHP, a LOT more! ===[/COLOR]

un  apache             <none>             (no description available)
un  apache-common      <none>             (no description available)
un  apache-ssl         <none>             (no description available)
un  apache-utils       <none>             (no description available)
un  apache2            <none>             (no description available)
un  apache2-common     <none>             (no description available)
un  apache2-doc        <none>             (no description available)
un  apache2-mpm        <none>             (no description available)
un  apache2-mpm-itk    <none>             (no description available)
ii  apache2-mpm-prefor 2.2.14-5ubuntu8    Apache HTTP Server - traditional non-threaded model
un  apache2-suexec     <none>             (no description available)
un  apache2-suexec-cus <none>             (no description available)
ii  apache2-utils      2.2.14-5ubuntu8    utility programs for webservers
ii  apache2.2-bin      2.2.14-5ubuntu8    Apache HTTP Server common binary files
ii  apache2.2-common   2.2.14-5ubuntu8    Apache HTTP Server common files

ii  mysql-client       5.1.41-3ubuntu12.3 MySQL database client (metapackage depending on the 
un  mysql-client-4.1   <none>             (no description available)
un  mysql-client-5.0   <none>             (no description available)
ii  mysql-client-5.1   5.1.41-3ubuntu12.3 MySQL database client binaries
ii  mysql-client-core- 5.1.41-3ubuntu12.3 MySQL database core client binaries
ii  mysql-common       5.1.41-3ubuntu12.3 MySQL database common files (e.g. /etc/mysql/my.cnf)
un  mysql-common-4.1   <none>             (no description available)
ii  mysql-server       5.1.41-3ubuntu12.3 MySQL database server (metapackage depending on the 
un  mysql-server-4.1   <none>             (no description available)
un  mysql-server-5.0   <none>             (no description available)
ii  mysql-server-5.1   5.1.41-3ubuntu12.3 MySQL database server binaries
un  mysql-server-core  <none>             (no description available)
un  mysql-server-core- <none>             (no description available)
ii  mysql-server-core- 5.1.41-3ubuntu12.3 MySQL database core server files

Does it look like I'm missing something?

---

### Post by WorMzy on 2010-07-07
Looks like you're missing a few of the PHP packages that I have, but have some that I don't. You're also missing the apache2 package, but I'm pretty sure that's just a placeholder package to make sure you're using the latest version.

PHP
```
ii  php5                           5.3.2-1ubuntu4.2               server-side, HTML-embedded scripting language (metapackage)
un  php5-cgi                       <none>                         (no description available)
ii  php5-common                    5.3.2-1ubuntu4.2               Common files for packages built from the php5 source
ii  php5-gd                        5.3.2-1ubuntu4.2               GD module for php5
un  php5-json                      <none>                         (no description available)
ii  php5-mcrypt                    5.3.2-0ubuntu1                 MCrypt module for php5
un  php5-mhash                     <none>                         (no description available)
ii  php5-mysql                     5.3.2-1ubuntu4.2               MySQL module for php5
un  php5-mysqli                    <none>                         (no description available)
un  php5-suhosin                   <none>                         (no description available)
```

APACHE
```
un  apache                         <none>                         (no description available)
un  apache-common                  <none>                         (no description available)
un  apache-ssl                     <none>                         (no description available)
un  apache-utils                   <none>                         (no description available)
ii  apache2                        2.2.14-5ubuntu8                Apache HTTP Server metapackage
un  apache2-common                 <none>                         (no description available)
un  apache2-doc                    <none>                         (no description available)
un  apache2-mpm                    <none>                         (no description available)
un  apache2-mpm-event              <none>                         (no description available)
un  apache2-mpm-itk                <none>                         (no description available)
ii  apache2-mpm-prefork            2.2.14-5ubuntu8                Apache HTTP Server - traditional non-threaded model
un  apache2-mpm-worker             <none>                         (no description available)
un  apache2-suexec                 <none>                         (no description available)
un  apache2-suexec-custom          <none>                         (no description available)
ii  apache2-utils                  2.2.14-5ubuntu8                utility programs for webservers
ii  apache2.2-bin                  2.2.14-5ubuntu8                Apache HTTP Server common binary files
ii  apache2.2-common               2.2.14-5ubuntu8                Apache HTTP Server common files
```

MySQL
```
ii  mysql-client                   5.1.41-3ubuntu12.3             MySQL database client (metapackage depending on the latest version)
un  mysql-client-4.1               <none>                         (no description available)
un  mysql-client-5.0               <none>                         (no description available)
ii  mysql-client-5.1               5.1.41-3ubuntu12.3             MySQL database client binaries
ii  mysql-client-core-5.1          5.1.41-3ubuntu12.3             MySQL database core client binaries
ii  mysql-common                   5.1.41-3ubuntu12.3             MySQL database common files (e.g. /etc/mysql/my.cnf)
un  mysql-common-4.1               <none>                         (no description available)
ii  mysql-server                   5.1.41-3ubuntu12.3             MySQL database server (metapackage depending on the latest version)
un  mysql-server-4.1               <none>                         (no description available)
un  mysql-server-5.0               <none>                         (no description available)
ii  mysql-server-5.1               5.1.41-3ubuntu12.3             MySQL database server binaries
un  mysql-server-core              <none>                         (no description available)
un  mysql-server-core-5.0          <none>                         (no description available)
ii  mysql-server-core-5.1          5.1.41-3ubuntu12.3             MySQL database core server files
```

---

### Post by fopetesl on 2010-07-07
The whole of my PHP files:```
un  php-pear           <none>             (no description available)
ii  php5               5.3.2-1ubuntu4.2   server-side, HTML-embedded scripting language (metap
ii  php5-cgi           5.3.2-1ubuntu4.2   server-side, HTML-embedded scripting language (CGI b
ii  php5-cli           5.3.2-1ubuntu4.2   command-line interpreter for the php5 scripting lang
ii  php5-common        5.3.2-1ubuntu4.2   Common files for packages built from the php5 source
un  php5-curl          <none>             (no description available)
ii  php5-dbg           5.3.2-1ubuntu4.2   Debug symbols for PHP5
ii  php5-dev           5.3.2-1ubuntu4.2   Files for PHP5 module development
un  php5-enchant       <none>             (no description available)
ii  php5-gd            5.3.2-1ubuntu4.2   GD module for php5
un  php5-gmp           <none>             (no description available)
un  php5-intl          <none>             (no description available)
un  php5-json          <none>             (no description available)
un  php5-ldap          <none>             (no description available)
ii  php5-mcrypt        5.3.2-0ubuntu1     MCrypt module for php5
un  php5-mhash         <none>             (no description available)
ii  php5-mysql         5.3.2-1ubuntu4.2   MySQL module for php5
un  php5-mysqli        <none>             (no description available)
un  php5-odbc          <none>             (no description available)
un  php5-pgsql         <none>             (no description available)
un  php5-pspell        <none>             (no description available)
un  php5-recode        <none>             (no description available)
un  php5-snmp          <none>             (no description available)
un  php5-sqlite        <none>             (no description available)
un  php5-suhosin       <none>             (no description available)
un  php5-sybase        <none>             (no description available)
un  php5-tidy          <none>             (no description available)
un  php5-xmlrpc        <none>             (no description available)
un  php5-xsl           <none>             (no description available)
un  phpapi-20090626+lf <none>             (no description available)
ii  phpmyadmin         4:3.3.2-1          MySQL web administration tool
```So I seem to have yours plus a few more!
Apache & MySQL look pretty similar also so it doesn't look like missing packages.
I'll spend some time comparing ini files.


Edit:
Another thought, WorMzy, have you actually attempted to 'call' a PHP script from an htm file loaded into Firefox?
I ask because it just may be something more basic than either of us have noticed.

---

### Post by WorMzy on 2010-07-07
Yeah, I made a small test page and script just before I posted my conf/ini files, just to make sure that a recent update hadn't been to blame or something. Worked perfectly.
test1.html:
```
<html>
  <head>
    <title>test</title>
  </head>
  <body>
    <form id="testform" action="process.php" method="get">
      <input type="text" name="testvar" />
      <input type="submit" />
    </form>
  </body>
</html>
```
process.php:
```
<?php
	print $_GET['testvar'];
?>
```

Works with either post or get.

There must be something in the config files, but I don't understand why it would only affect that php file and not others.

I ruled out an error in the php, because it doesn't display a blank page/error page (depending on your configuration), so that suggests it's not processing PHP, but it clearly is.

Just a thought, you do have <?php and ?> tags surrounding the php code, right? and the file extension is ".php" (I'm pretty sure it is, since that's what your HTML called for, and you're not getting a 404)

---

### Post by fopetesl on 2010-07-08
> **WorMzy said:**
> Yeah, I made a small test page and script just ...

Just a thought, you do have <?php and ?> tags surrounding the php code, right? and the file extension is ".php" (I'm pretty sure it is, since that's what your HTML called for, and you're not getting a 404)Yes tags are correct. One of the first things I checked - original processData.php written in PHP4 - didn't have to change much to remove PHP5 warnings.

Now, from usalug.org forum, I had a suggestion:[quote="mushroom"][quote="fopetesl"] restarted apache and re-ran [color=blue]test.htm[/color]
```
<form action="processData.php" method="post"> 
```[/quote]
You could try
```
<form action="http://localhost/processData.php" method="post"> 
```
I have for many years now included the full path in my "form action", I can't remember why I started doing it.[/quote]and after moving the test.htm and processData.php into /var/www/, s*d me, it works!```
&result1=**success**&result2=1-METER;5-USB STICK&#65533;
```
(Hook=1 is a request for available data sources).

However if I keep test.htm in /var/www/, move processData.php back into /var/www/html/ and edit the line to read```
<form action="http://localhost/html/processData.php" method="post"> 
```I get the response```
&result1=**failure**&error=CANNOT OPEN LOG FILE!
```The PHP code that fails:```
      case   1 :  // RETURN ALL  AVAILABLE DATA  SOURCES :
                   //   1-METER
                   //   2-CD
                   //   3-FLOPPY
                   //   4-NETWORK (NEEDED?)

    $FDATA = fopen("scaninf.log","w+");
    if( !$FDATA) {
      echo "&result1=**failure**&error=CANNOT OPEN LOG FILE!";
      exit(0);
    }
    fwrite( $FDATA,"scaninf Case 1 open\n");
```OOOPS! :redface: Not the PHP code! Permissions on scaninf.log :(

Then I moved test.htm back into /var/www/html and ran it again and it still works! :)

The bottom line seems to be that Apache (Firefox?) will not look into /var/www/html and see a real PHP file unless it's explicitly told to.

Did you put your test scripts in /var/www/ or /var/www/html/?

This is not an answer for me to edit the //localhost line :(
Hard coded into the Flash GUI must be the same command as issued by test.htm.   I have no means or capability to edit the Flash code.

---

### Post by WorMzy on 2010-07-08
I had my test code in /var/www, but I can't seem to recreate the problem after putting it in /var/www/html, so I still think that there's probably something different between our config files that's causing this behaviour.

It never would have occurred to me to use full paths, I'd have only thought that that wouldn't help unless you weren't using a localhost address to access your html file.

---

### Post by fopetesl on 2010-07-08
That's today sorted then.  I'll compare our .ini files.

BTW, your cat is unusual :)  I like cats even when they decimate my garden birds.

And you have some serious hardware :mrgreen:

---

### Post by WorMzy on 2010-07-08
Haha, it's Shii, the singing box cat. :p

Unfortunately, my hardware list needs updating, Sakura has been left a shadow of her former self. Long story short, my water-based CPU heatsink exploded and poured coolant all over my motherboard and GPU, so now the mobo is half-dead and won't even power up, the GPU's RAM is damaged (causes artefacts after about 10 minutes), and the heatsink is only useful as a paperweight. Fortunately I had backup hardware, but it's not even nearly as good.

Anyway, good luck finding the problem; this has been one of the weirdest problems I've encountered and tried to help with. I've had similar problems involving cgi-bin directories and scripts, but never with php.

---

### Post by fopetesl on 2010-07-08
Right! I found time to compare our php.ini files.  If they are not mirrors then I couldn't see any difference :)
Tomorrow apache and hopefully MySQL....

I had this response from usalug.org> [quote]fopetesl wrote:
Did you put your test scripts in /var/www/ or /var/www/html/?

I put all my test scripts in my home folder "/home/user_name/public_html/project_folder", it makes editing them convenient. :idea:
To make them work, I as root edited "/etc/apache2/default-server.conf"
```
Options FollowSymLinks
```

then I put a symlink for each project_folder in the DocumentRoot as defined in "/etc/apache2/default-server.conf".

You must put all your scripts or symlinks in the folder defined as DocumentRoot in "/etc/apache2/default-server.conf" or apache will not find them.[/quote]Interesting that.  I've never used symlinks so it's RTFM tomorrow..

P.S. You don't actually have a cat then (or it has you) just an iPod?
P.P.S. I have as few as possible fans in my kit.  Fanless graphics and mobos where ever possible.

---

### Post by WorMzy on 2010-07-08
Nah, no cat. No iPod either, can't stand Apple hardware (or software for that matter). I have a Creative Zen instead. ;)

I have follow symlinks in my config, so maybe it's that. I can't see how it's make much difference though, unless you're storing the files outside of the host directories, or maybe apache just has a different interpretation to me over what symlinks are.

---

### Post by fopetesl on 2010-07-09
[quote="mushroom"][quote="fopetesl"]
To make them work, I as root edited "/etc/apache2/default-server.conf"
```
Options FollowSymLinks
```
then I put a symlink for each project_folder in the DocumentRoot as defined in  "/etc/apache2/default-server.conf".[/quote]Hmmm. Except I don't have "/etc/apache2/default-server.conf"```
/etc/apache2# ls -l
total 72
-rw-r--r-- 1 root root  8133 2010-07-07 10:44 apache2.conf
drwxr-xr-x 2 root root  4096 2010-07-04 13:17 conf.d
-rw-r--r-- 1 root root   725 2010-04-13 20:27 envvars
-rw-r--r-- 1 root root    21 2010-07-06 16:27 httpd.conf
-rw-r--r-- 1 root root 31063 2010-04-13 20:27 magic
drwxr-xr-x 2 root root  4096 2010-07-04 12:53 mods-available
drwxr-xr-x 2 root root  4096 2010-07-04 12:53 mods-enabled
-rw-r--r-- 1 root root   750 2010-04-13 20:27 ports.conf
drwxr-xr-x 2 root root  4096 2010-07-04 12:52 sites-available
drwxr-xr-x 2 root root  4096 2010-07-04 12:53 sites-enabled
``` Anywhere :(

Is this supposed to be created automagically or do I have to create it?

EDIT ======

There IS something similar in /etc/apache2/sites-available```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```so I assumed this is the file?
So I created a symlink in /var/www```
/var/www$ ls -l
total 20
-r--r--r-- 1 meter meter 3638 2006-06-19 12:24 favicon.ico
-rw-r--r-- 1 root    root       0 2007-06-18 11:18 Hauteur.log
drwxr--rwx 6 meter meter 4096 2010-07-08 10:26 html
-rw-r--r-- 1 root    root     177 2010-07-04 12:53 index.html
lrwxrwxrwx 1 meter meter   13 2010-07-09 13:14 Link to html -> /var/www/html
-rw-rw-rw- 1 meter meter    1 2010-07-08 10:04 scaninf.log
-rw-r--r-- 1 root    root      19 2010-07-06 16:20 test.php
```But still no joy. Same "what to do with this file" from Apache/Firefox :(

---

### Post by WorMzy on 2010-07-09
You don't think it could have something to do with ownership do you? You've got root owned documents mixed in with meter owned documents, the root owned "test.php" worked fine, so maybe try chowning processData.php to root, if it isn't already?

---

### Post by fopetesl on 2010-07-09
Don't think it's an ownership problem since if I move processData.php into /var/www it works OK.  Without changing permissions or owner:group.

I tried to change owner:group of [COLOR="Blue"]Link to html[/COLOR] on CLI (as root) but it won't change using [COLOR="Blue"]/var/www# chown root:root Link\ to\ html[/COLOR] with no error message.

Is it the spaces causing a problem?

EDIT==
Managed to rename to htmlink but still same problem.
Still cannot change owner:group either of this symlink.

EDIT(2) ==
I changed ownership and permissions every which way I could think of as per your suggestion but no change :(

---

### Post by WorMzy on 2010-07-09
I'd just like to confirm that you're accessing the files through [http://localhost/]("http://localhost/"), and not [file:///var/www/]("file:///var/www/"), right? I'm still not sure why using the full path in the html form's action is working, but not a relative path, and opening the file through file:/// is the only thing that I can think of which would cause a change in behaviour.

---

### Post by fopetesl on 2010-07-10
> **WorMzy said:**
> I'd just like to confirm that you're accessing the files through [http://localhost/]("http://localhost/"), and not [file:///var/www/]("file:///var/www/"), right? I'm still not sure why using the full path in the html form's action is working, but not a relative path, and opening the file through file:/// is the only thing that I can think of which would cause a change in behaviour.

Not sure I fully understand your question. Remember that```
<form action="processData.php" method="post">

``` doesn't work but```
<form action="http://localhost/html/processData.php" method="post">

```does.

I don't know whether the first (failure) example does access localhost// or file://
Is there any way to check?

I also found this from [http://httpd.apache.org/docs/2.2/mod/core.html](http://httpd.apache.org/docs/2.2/mod/core.html) > <Directory> and </Directory> are used to enclose a group of directives that will apply only to the named directory and sub-directories of that directory. Any directive that is allowed in a directory context may be used. Directory-path is either the full path to a directory, or a wild-card string using Unix shell-style matching. In a wild-card string, ? matches any single character, and * matches any sequences of characters. You may also use [] character ranges. None of the wildcards match a `/' character, so <Directory /*/public_html> will not match /home/user/public_html, but <Directory /home/*/public_html> will match. Example:

<Directory /usr/local/httpd/htdocs>
Options Indexes FollowSymLinks
</Directory>

Be careful with the directory-path arguments: They have to literally match the filesystem path which Apache uses to access the files. Directives applied to a particular <Directory> will not apply to files accessed from that same directory via a different path, such as via different symbolic links.

Regular expressions can also be used, with the addition of the ~ character. For example:

<Directory ~ "^/www/.*/[0-9]{3}">

would match directories in /www/ that consisted of three numbers.but I couldn't get any combination to work even using Regular expressions.
All I got when restarting Apache was "directory doesn't exist".
Probably my poor syntax.
What I was attempting to do was to get Apache to look also in ../html so I don't have to be explicit with the direction.
I don't know if you have any experience with Regular expression but maybe you can suggest something?

Also how do I get to examine the /html directory's owner:group and permissions?
If I am in /var/www and [COLOR="Blue"]..# ls -ld[/COLOR] all I get is current directory information.

---

### Post by WorMzy on 2010-07-10
What I meant was, are you accessing the html page/flash UI in firefox by going to [http://localhost/html/test.htm]("http://localhost/html/test.htm"), or are you opening them by double clicking on them/browsing to them through file://?

If you're accessing through localhost, then the action's relative address will be interpreted as a localhost address (e.g. [http://localhost/html/processData.php](http://localhost/html/processData.php)) and the PHP (should) be processed as normal, but if you're accessing through file://, then the relative address will also be interpreted as a file:// address, apache won't be involved with the serving of the page and, as such, the PHP won't be processed.

If you access the html/flash UI through file:// and set the action's address to a fullpath to a localhost address, then apache will serve the page and the PHP will be processed.

That's the only reason I can see for the full path and relative path having different effects.

> Also how do I get to examine the /html directory's owner:group and permissions?
If I am in /var/www and ..# ls -ld all I get is current directory information.

ls -l html
or cd into html and rerun ls -l

I don't have much experience with regex, I've made a couple of statements to use in various programs, but only after starting at various help pages for hours.

---

### Post by fopetesl on 2010-07-10
I see your point.
However [COLOR="Blue"]http://localhost/html/test.htm[/COLOR] works and the sub-call to processData.php works.
Just like the situation where test.htm & processData.php are in /var/www.

Unhappily [COLOR="Red"]http://localhost/test.htm[/COLOR] doesn't.  Says can't find the file.

Apache obviously isn't looking into html.

If I```
root@Almeter-AL2ooo:/var/www# ls -l
total 20
-r--r--r-- 1 meter meter 3638 2006-06-19 12:24 favicon.ico
-rw-rw-rw- 1 meter meter    0 2007-06-18 11:18 Hauteur.log
drwxrwxrwx 6 meter meter 4096 2010-07-08 10:26 html
lrwxrwxrwx 1 meter meter   13 2010-07-09 13:14 htmlink -> /var/www/html
-rw-r--r-- 1 root    root     177 2010-07-04 12:53 index.html
lrwxrwxrwx 1 meter meter   29 2010-07-09 17:09 processData.php -> /var/www/html/processData.php
-rw-rw-rw- 1 meter meter    1 2010-07-08 10:04 scaninf.log
-rw-r--r-- 1 root    root      19 2010-07-06 16:20 test.php
```
So .../html is there and has the right stats?  Also the symlink htmlink.

---

### Post by WorMzy on 2010-07-10
I'm not on Lucid at the moment, but here's my ls -l of it's /var/www:
```
wormzy@sakura:~$ ls -l /media/Lucid/var/www
total 160
-rw-r--r-- 1 root root 94300 Jul  8 11:23 access.log
drwxr-xr-x 2 root root  4096 May 13 05:04 cgi-bin
drwxr-xr-x 2 root root  4096 May 13 05:09 doc
-rw-r--r-- 1 root root 21881 Jul  8 11:23 error.log
-rw-r--r-- 1 root root  1421 May 10 12:10 getrss.php
drwxr-xr-x 2 root root  4096 Jul  8 11:23 html
-rw-r--r-- 1 root root    20 May  6 07:03 indexdc.php
-rw-r--r-- 1 root root   177 Apr 30 17:30 index.html
-rw-r--r-- 1 root root    20 Jul  7 11:47 phptest.php
-rw-r--r-- 1 root root    44 Jul  7 13:05 process.php
-rw-r--r-- 1 root root   214 Jul  7 13:03 test1.html
-rw-r--r-- 1 root root   915 May 10 12:13 test.html

```

Different permissions all around, but I doubt they have much bearing on apache's behaviour, so long as the http user has read rights on all files and can access the /var/www folder, then all other ownership/permissions are disregarded (AFAIK).

I'm all out of ideas now. There seems to be something bizarre going on with your machine. You might want to consider purging apache, php, and everything related to them, then 'sudo rm -fr'-ing /etc/apache2 and /etc/php5, [maybe backup the files you want to keep, then 'sudo rm -fr' /var/www, before remaking it with 'sudo mkdir'], then reinstalling a fresh copy of apache and php.

---

