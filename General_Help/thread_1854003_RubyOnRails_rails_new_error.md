---
title: "RubyOnRails rails new error"
date: 2011-10-03
forum: General Help
---

### Post by mao3 on 2011-10-03
Hey,  I'm following the RubyOnRails - Communtiy Ubuntu Documentation here [https://help.ubuntu.com/community/RubyOnRails](https://help.ubuntu.com/community/RubyOnRails) and I ran into a problem in "Preparing for your first rail app".  Trying to run this command in the terminal ```
rails /home/myuser/www/mynewapp
``` gave me the following error ```
Gem::Installer::ExtensionBuildError: ERROR: Failed to build gem native extension.

        /usr/bin/ruby1.8 extconf.rb 
checking for sqlite3.h... no
sqlite3.h is missing. Try 'port install sqlite3 +universal'
or 'yum install sqlite3-devel' and check your shared library search path (the
location where your sqlite3 shared library is located).
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
    --ruby=/usr/bin/ruby1.8
    --with-sqlite3-dir
    --without-sqlite3-dir
    --with-sqlite3-include
    --without-sqlite3-include=${sqlite3-dir}/include
    --with-sqlite3-lib
    --without-sqlite3-lib=${sqlite3-dir}/lib
    --enable-local
    --disable-local


Gem files will remain installed in /home/miguel/.bundler/tmp/13636/gems/sqlite3-1.3.4 for inspection.
Results logged to /home/miguel/.bundler/tmp/13636/gems/sqlite3-1.3.4/ext/sqlite3/gem_make.out
An error occured while installing sqlite3 (1.3.4), and Bundler cannot continue.
Make sure that `gem install sqlite3 -v '1.3.4'` succeeds before bundling.
```

I did run the command ```
sudo gem install sqlite3 -v '1.3.4'
``` but it gave me a similar error to the one above, saying the header file was missing and I should try the yum or port command.  So, I tried the port command first and got a port command not found error.  I installed yum and tried the yum command and got the following error ```
sudo yum install sqlite3-devel
Setting up Install Process
No package sqlite3-devel available.
Nothing to do
```

Does anyone know how to fix this?  Any help would be appreciated.

---

### Post by seawolf167 on 2011-10-04
I don't know RubyOnRails nor do I use it, but, do you have all the items listed [here]("https://help.ubuntu.com/community/RubyOnRails#Get_Ruby") installed?

You might also need to install

```
sudo apt-get install linux-headers-X.X.XX-XX-generic
```where you can get the X's by entering the command

```
uname -a
```

Also, what is the output of the file "mkmf.log"

---

### Post by mao3 on 2011-10-05
Hey, 

thank you for replying.  I did the aptitude install because I only wanted the essential packages, so I didn't do a ruby-full install.  Also, I didn't install any server since Ruby already comes with WEBrick and I figured I would stick with that for now.    

I entered the commands you provided, but it didn't make any changes and said I was up to date.    I decided to try using mysql to see if that would do anything differently, but it didn't.  

Here is my mkmf.log file found in /usr/lib/ruby/gems/1.8/gems/mysql2-0.3.7/ext/mysql2.  Let me know if you wanted to see another mkmf.log file because I think there's a couple more in other folders.```
have_func: checking for rb_thread_blocking_region()... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I.    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘rb_thread_blocking_region’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))rb_thread_blocking_region; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I.    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/tmp/cc4Zgk5a.o: In function `t':
/usr/lib/ruby/gems/1.8/gems/mysql2-0.3.7/ext/mysql2/conftest.c:3: undefined reference to `rb_thread_blocking_region'
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { rb_thread_blocking_region(); return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lmysqlclient  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

have_library: checking for main() in -lm... -------------------- yes

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic     -lruby1.8-static -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))main; return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lmysqlclient -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

have_library: checking for main() in -lz... -------------------- yes

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lm  -lruby1.8-static -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))main; return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

have_library: checking for main() in -lsocket... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lsocket -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lsocket
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))main; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lsocket -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lsocket
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { main(); return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lmysqlclient -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

have_library: checking for main() in -lnsl... -------------------- yes

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lz -lm  -lruby1.8-static -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))main; return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

have_library: checking for main() in -lmygcc... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmygcc -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmygcc
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))main; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmygcc -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmygcc
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { main(); return 0; }
/* end */

--------------------

find_library: checking for mysql_query() in -lmysqlclient... -------------------- no

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
conftest.c: In function ‘t’:
conftest.c:3:53: error: ‘mysql_query’ undeclared (first use in this function)
conftest.c:3:53: note: each undeclared identifier is reported only once for each function it appears in
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))mysql_query; return 0; }
/* end */

"gcc -o conftest -I. -I/usr/lib/ruby/1.8/x86_64-linux -I. -I/usr/local/include    -fno-strict-aliasing -g -g -O2  -fPIC   conftest.c  -L. -L/usr/lib -L/usr/local/lib -L/usr/local/lib/mysql -L. -Wl,-Bsymbolic-functions -rdynamic -Wl,-export-dynamic    -lnsl -lz -lm  -lruby1.8-static -lmysqlclient -lnsl -lz -lm  -lpthread -lrt -ldl -lcrypt -lm   -lc"
/usr/bin/ld: cannot find -lmysqlclient
collect2: ld returned 1 exit status
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { mysql_query(); return 0; }
/* end */

--------------------

```

---

### Post by seawolf167 on 2011-10-05
It looks like you may need to [install mysql]("https://help.ubuntu.com/10.04/serverguide/C/mysql.html")? I know you said you did, but according to the log, all the errors returned are referencing mysql

```
...
error: &#8216;mysql_query&#8217; undeclared
...
cannot find -lmysqlclient
...
```Again, I don't use Ruby at all, so these are just my guesses.

---

### Post by mao3 on 2011-10-05
I did install it, I actually looked at that link you provided when I installed it, but maybe it's not looking for files in the correct location?  Is there a way I can make it look in the right place?  Do I have to configure something?

---

### Post by mao3 on 2011-10-05
I fixed it, so the problem was that, although I did install the mysql server, I didn't install some other things I needed.  The step right below preparing your first app should really be above that because it tells you how to configure your server for ruby.  So I just had to type the following commands ```
sudo apt-get install mysql-client sudo apt-get install libmysql-ruby libmysqlclient-dev sudo gem install mysql
```

And then it worked :D, I got the following message after the command ```
rails new ~/www/mynewapp -d mysql
``` at the very end :```
Your bundle is complete! Use `bundle show [gemname]` to see where a bundled gem is installed.

```

---

### Post by seawolf167 on 2011-10-05
Glad you got it figured out! Hopefully it'll help anyone else that runs into the same problem.

---

### Post by Bor1s on 2011-11-14
Thank you sir! This was most helpful as I was too fighting this very problem.

---

