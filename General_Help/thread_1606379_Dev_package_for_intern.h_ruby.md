---
title: "Dev package for intern.h ruby"
date: 2010-10-26
forum: General Help
---

### Post by redlinethecar on 2010-10-26
Hello I am currently trying to get my RadRails working. There are certain tasks I cannot complete and I'm guessing that installing mongrel and some other items would get everything going. I run the update and it seems to fail horribly and I've been looking on google for the last 2 hours to the answer to this one. This is there errors I have gotten so far.

By the way I am currently using Ubuntu 10.04 if that makes any difference. I have already downloaded and installed sqlite3 and sqlite dev. 

```
>gem install -l mongrel-1.1.5.gem
Building native extensions.  This could take a while...
ERROR:  Error installing mongrel-1.1.5.gem:
    ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb
checking for main() in -lc... yes
creating Makefile

make
gcc -I. -I/usr/local/include/ruby-1.9.1/x86_64-linux -I/usr/local/include/ruby-1.9.1/ruby/backward -I/usr/local/include/ruby-1.9.1 -I.   -fPIC -O3 -ggdb -Wextra -Wno-unused-parameter -Wno-parentheses -Wpointer-arith -Wwrite-strings -Wno-missing-field-initializers -Wno-long-long  -o http11.o -c http11.c
http11.c: In function ‘http_field’:
http11.c:70: warning: format not a string literal and no format arguments
http11.c:71: warning: format not a string literal and no format arguments
http11.c:77: error: ‘struct RString’ has no member named ‘ptr’
http11.c:77: error: ‘struct RString’ has no member named ‘len’
http11.c: In function ‘request_uri’:
http11.c:102: warning: format not a string literal and no format arguments
http11.c: In function ‘fragment’:
http11.c:113: warning: format not a string literal and no format arguments
http11.c: In function ‘request_path’:
http11.c:124: warning: format not a string literal and no format arguments
http11.c: In function ‘query_string’:
http11.c:135: warning: format not a string literal and no format arguments
http11.c: In function ‘header_done’:
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:172: error: ‘struct RString’ has no member named ‘ptr’
http11.c:174: error: ‘struct RString’ has no member named ‘ptr’
http11.c:176: error: ‘struct RString’ has no member named ‘ptr’
http11.c:177: error: ‘struct RString’ has no member named ‘len’
http11.c: In function ‘HttpParser_execute’:
http11.c:298: error: ‘struct RString’ has no member named ‘ptr’
http11.c:299: error: ‘struct RString’ has no member named ‘len’
http11.c:307: warning: format not a string literal and no format arguments
make: *** [http11.o] Error 1


Gem files will remain installed in /usr/local/lib/ruby/gems/1.9.1/gems/mongrel-1.1.5 for inspection.
Results logged to /usr/local/lib/ruby/gems/1.9.1/gems/mongrel-1.1.5/ext/http11/gem_make.out
>gem install -l sqlite3-ruby-1.2.1.gem
Building native extensions.  This could take a while...
ERROR:  Error installing sqlite3-ruby-1.2.1.gem:
    ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb
checking for sqlite3.h... yes
checking for sqlite3_open() in -lsqlite3... yes
creating Makefile

make
gcc -I. -I/usr/local/include/ruby-1.9.1/x86_64-linux -I/usr/local/include/ruby-1.9.1/ruby/backward -I/usr/local/include/ruby-1.9.1 -I. -DHAVE_SQLITE3_H -I/usr/local/include    -fPIC -O3 -ggdb -Wextra -Wno-unused-parameter -Wno-parentheses -Wpointer-arith -Wwrite-strings -Wno-missing-field-initializers -Wno-long-long  -o sqlite3_api_wrap.o -c sqlite3_api_wrap.c
In file included from sqlite3_api_wrap.c:1058:
/usr/local/include/ruby-1.9.1/ruby/backward/rubyio.h:2:2: warning: #warning use "ruby/io.h" instead of "rubyio.h"
sqlite3_api_wrap.c:1066:20: error: intern.h: No such file or directory
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_complete16’:
sqlite3_api_wrap.c:1412: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_trace’:
sqlite3_api_wrap.c:1492: warning: cast from pointer to integer of different size
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_open’:
sqlite3_api_wrap.c:1509: warning: assignment makes pointer from integer without a cast
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_open16’:
sqlite3_api_wrap.c:1537: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_prepare’:
sqlite3_api_wrap.c:1627: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:1628: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_prepare16’:
sqlite3_api_wrap.c:1663: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:1664: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_bind_blob’:
sqlite3_api_wrap.c:1702: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:1703: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_bind_text’:
sqlite3_api_wrap.c:1808: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:1809: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_bind_text16’:
sqlite3_api_wrap.c:1834: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:1835: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_create_function16’:
sqlite3_api_wrap.c:2289: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_blob’:
sqlite3_api_wrap.c:2531: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2532: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_error’:
sqlite3_api_wrap.c:2566: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2567: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_error16’:
sqlite3_api_wrap.c:2585: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2586: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_text’:
sqlite3_api_wrap.c:2637: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2638: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_text16’:
sqlite3_api_wrap.c:2658: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2659: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_text16le’:
sqlite3_api_wrap.c:2679: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2680: error: ‘struct RString’ has no member named ‘len’
sqlite3_api_wrap.c: In function ‘_wrap_sqlite3_result_text16be’:
sqlite3_api_wrap.c:2700: error: ‘struct RString’ has no member named ‘ptr’
sqlite3_api_wrap.c:2701: error: ‘struct RString’ has no member named ‘len’
make: *** [sqlite3_api_wrap.o] Error 1


Gem files will remain installed in /usr/local/lib/ruby/gems/1.9.1/gems/sqlite3-ruby-1.2.1 for inspection.
Results logged to /usr/local/lib/ruby/gems/1.9.1/gems/sqlite3-ruby-1.2.1/ext/sqlite3_api/gem_make.out
>gem install -l linecache-0.43.gem
Building native extensions.  This could take a while...
ERROR:  Error installing linecache-0.43.gem:
    ERROR: Failed to build gem native extension.

/usr/local/bin/ruby extconf.rb
Can't handle 1.9.x yet
*** extconf.rb failed ***
Could not create Makefile due to some reason, probably lack of
necessary libraries and/or headers.  Check the mkmf.log file for more
details.  You may need configuration options.

Provided configuration options:
    --with-opt-dir
    --without-opt-dir
    --with-opt-include
    --without-opt-include=${opt-dir}/include
    --with-opt-lib
    --without-opt-lib=${opt-dir}/lib
    --with-make-prog
    --without-make-prog
    --srcdir=.
    --curdir
    --ruby=/usr/local/bin/ruby


Gem files will remain installed in /usr/local/lib/ruby/gems/1.9.1/gems/linecache-0.43 for inspection.
Results logged to /usr/local/lib/ruby/gems/1.9.1/gems/linecache-0.43/ext/gem_make.out
>gem install -l ruby-debug-base-0.10.3.gem
ERROR:  Error installing ruby-debug-base-0.10.3.gem:
    ruby-debug-base requires linecache (>= 0.3, )
>gem install -l ruby-debug-ide-0.4.5.gem
ERROR:  Error installing ruby-debug-ide-0.4.5.gem:
    ruby-debug-ide requires ruby-debug-base (~> 0.10.3.0, runtime)
>
```

Now at this point I am just trying to find the intern.h header file and can't find out what to download to get that. If anyone could assist me or point me to the right direction I would really appreciate it.

---

### Post by gmargo on 2010-10-26
> **redlinethecar said:**
> Now at this point I am just trying to find the **intern.h** header file and can't find out what to download to get that.

If you're looking for a file that you believe to be an ubuntu-distributed file, use the packages web site: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

The second text box on the page is to "Search the contents of packages".  Enter "intern.h" and select your distribution as "Lucid", and hit the "Search" button.  Here's a link to that: [http://packages.ubuntu.com/search?searchon=contents&keywords=intern.h&mode=exactfilename&suite=lucid&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=intern.h&mode=exactfilename&suite=lucid&arch=any)

It will give a nice table that tells you that intern.h is available in one of several packages.  You will probably need to install the _**[ruby1.9.1-dev]("http://packages.ubuntu.com/lucid/ruby1.9.1-dev")**_ (or ruby-1.9-dev) package.

---

### Post by redlinethecar on 2010-10-26
Thank you that help. Didn't solve the problem but solved a small part of it. I just can't figure out why they would make it so hard to use ruby on rails for linux. It appears a lot of people are having issues with this.

---

