---
title: "&quot;Make&quot; Error 1/2 Installing Thrift on Ubuntu"
date: 2010-11-04
forum: General Help
---

### Post by kv_flock on 2010-11-04
[SIZE=2]Relatively new user of Ubuntu trying to get flockDB (limited info here: [https://github.com/twitter/flockdb](https://github.com/twitter/flockdb)) up and running. Unfortunately there's a couple pre-reqs (Java, sbt, Ruby, gizzmo, etc) including Apache Thrift 0.2.0 (NOT the most recent version of Thrift 0.5.0).

The trouble I'm running into is with the "make" portion of my installation. I've managed to get through the configuration, but when I try to make, I get the error below.[/SIZE]


root@kv-VirtualBox:/home/kv/Downloads/thrift-0.2.0# make
make  all-recursive
make[1]: Entering directory `/home/kv/Downloads/thrift-0.2.0'
Making all in compiler/cpp
make[2]: Entering directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
Regenerating version.h... No changes.
make  all-am
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
\
     \
    /bin/bash ../../ylwrap `test -f 'src/thriftl.ll' || echo  './'`src/thriftl.ll .c thriftl.cc -- /bin/bash  /home/kv/Downloads/thrift-0.2.0/missing --run flex  
make[3]: *** [thriftl.cc] Error 1
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kv/Downloads/thrift-0.2.0'
make: *** [all] Error 2[SIZE=2]

As far as I can tell, Error 2 is just a catch-all, and it seems like the problem might be that I'm somehow missing flex (?) but I have it installed: [/SIZE]

root@kv-VirtualBox:/home/kv/Downloads/thrift-0.2.0# which flex
/usr/bin/flex

[SIZE=2]Anybody have any thoughts on what the problem here might be? I'd appreciate any help.[/SIZE]

---

### Post by kv_flock on 2010-11-04
[SIZE=2]Okay, so I rechecked my flex/bison and made sure all my versions were up-to-date, also made sure I had the python-dev package installed (already had python) and then reconfigured. That seems to have dealt with the last problem. 

Unfortunately, I now get a similar but different error. Looks like it may be something with mkmf? I have no idea... I'd love to hear any advice/recommendations/thoughts, otherwise I guess I'll just keep updating this as I go along, so anyone else who runs into these problems will have a reference...

Current error looks like:

[SIZE=1]root@kv-VirtualBox:/home/kv/Downloads/thrift-0.2.0# make
make  all-recursive
make[1]: Entering directory `/home/kv/Downloads/thrift-0.2.0'
Making all in compiler/cpp
make[2]: Entering directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
Regenerating version.h... No changes.
make  all-am
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
make[2]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
Making all in lib
make[2]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib'
Making all in cpp
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib/cpp'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib/cpp'
Making all in py
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib/py'
/usr/bin/python setup.py build
running build
running build_py
running build_ext
building 'thrift.protocol.fastbinary' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -I/usr/include/python2.6 -c src/protocol/fastbinary.c -o build/temp.linux-i686-2.6/src/protocol/fastbinary.o
gcc -pthread -shared -Wl,-O1 -Wl,-Bsymbolic-functions build/temp.linux-i686-2.6/src/protocol/fastbinary.o -o build/lib.linux-i686-2.6/thrift/protocol/fastbinary.so
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib/py'
Making all in erl
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib/erl'
for dir in src; do \
        (cd $dir; make all); \
    done
make[4]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib/erl/src'
mkdir ../ebin
   ERLC  thrift_binary_protocol.erl
   ERLC  thrift_protocol.erl
   ERLC  thrift_socket_server.erl
   ERLC  test_handler.erl
   ERLC  thrift_memory_buffer.erl
   ERLC  thrift_http_transport.erl
   ERLC  thrift_client.erl
   ERLC  thrift_framed_transport.erl
   ERLC  thrift_transport.erl
   ERLC  thrift_socket_transport.erl
   ERLC  test_service.erl
   ERLC  thrift_processor.erl
   ERLC  thrift_buffered_transport.erl
   ERLC  thrift_base64_transport.erl
   ERLC  thrift_service.erl
   ERLC  thrift_server.erl
   ERLC  thrift_disk_log_transport.erl
   ERLC  thrift_file_transport.erl
sed -e 's;%VSN%;0.1;' \
        -e 's;%PFX%;thrift;' \
        -e 's;%APP_NAME%;thrift;' \
        -e 's;%MODULES%;%MODULES%"thrift_binary_protocol", "thrift_protocol", "thrift_socket_server", "test_handler", "thrift_memory_buffer", "thrift_http_transport", "thrift_client", "thrift_framed_transport", "thrift_transport", "thrift_socket_transport", "test_service", "thrift_processor", "thrift_buffered_transport", "thrift_base64_transport", "thrift_service", "thrift_server", "thrift_disk_log_transport", "thrift_file_transport",;' \
        thrift.app.src > thrift.app.src".tmp"
sed -e 's/%MODULES%\(.*\),/\1/' \
        thrift.app.src".tmp" > ../ebin/thrift.app
rm thrift.app.src".tmp"
sed -e 's;%VSN%;0.1;' thrift.appup.src > ../ebin/thrift.appup
make[4]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib/erl/src'
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib/erl'
Making all in rb
make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/lib/rb'
/usr/bin/ruby setup.rb config
---> lib
---> lib/thrift
---> lib/thrift/transport
<--- lib/thrift/transport
---> lib/thrift/core_ext
<--- lib/thrift/core_ext
---> lib/thrift/serializer
<--- lib/thrift/serializer
---> lib/thrift/protocol
<--- lib/thrift/protocol
---> lib/thrift/server
<--- lib/thrift/server
<--- lib/thrift
<--- lib
---> ext
/usr/bin/ruby1.8 /home/kv/Downloads/thrift-0.2.0/lib/rb/ext/extconf.rb
/home/kv/Downloads/thrift-0.2.0/lib/rb/ext/extconf.rb:20:in `require': no such file to load -- mkmf (LoadError)
    from /home/kv/Downloads/thrift-0.2.0/lib/rb/ext/extconf.rb:20
setup.rb:655:in `command': system("/usr/bin/ruby1.8" "/home/kv/Downloads/thrift-0.2.0/lib/rb/ext/extconf.rb") failed (RuntimeError)
    from setup.rb:660:in `ruby'
    from setup.rb:1238:in `extconf'
    from setup.rb:1230:in `config_dir_ext'
    from setup.rb:1532:in `__send__'
    from setup.rb:1532:in `traverse'
    from setup.rb:1549:in `dive_into'
    from setup.rb:1530:in `traverse'
    from setup.rb:1524:in `exec_task_traverse'
    from setup.rb:1519:in `each'
    from setup.rb:1519:in `exec_task_traverse'
    from setup.rb:1223:in `exec_config'
    from setup.rb:991:in `exec_config'
    from setup.rb:826:in `__send__'
    from setup.rb:826:in `invoke'
    from setup.rb:773:in `invoke'
    from setup.rb:1578
make[3]: *** [all-local] Error 1
make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib/rb'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/lib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kv/Downloads/thrift-0.2.0'
make: *** [all] Error 2
[/SIZE]
[/SIZE]

---

### Post by kv_flock on 2010-11-04
[SIZE=2][FONT=Arial][SIZE=3]Okay, I don't know what exactly did the trick, and I'm not a scientist enough to go back and try it one by one, but I ended up deciding I was probably missing some xyz-dev package, so I went through and reinstalled *everything* and it worked!

If anybody else is trying to reproduce, these are what I re-installed:[/SIZE][/FONT]

[/SIZE][FONT=Arial]sudo apt-get install libboost-dev 
sudo apt-get install libboost-test1.40-dev 
sudo apt-get install libevent-dev 
sudo apt-get install libtool
sudo apt-get install ruby-dev  
sudo apt-get install librspec-ruby
sudo apt-get install rake
sudo apt-get install rubygems
sudo apt-get install python-dev  
sudo apt-get install python-twisted
sudo apt-get install libbit-vector-perl
sudo apt-get install php5-dev
sudo apt-get install php5-cli

[SIZE=3]and so on and so on with[/SIZE] libglib2.0-dev, erlang-base, mono-gmcs,
libmono-dev, ghc6, cabal-install, libghc6-binary-dev, 
libghc6-network-dev, libghc6-http-dev
[/FONT][SIZE=2][FONT=Arial][SIZE=3]
And then I also double checked that I had the GNU Scientific Library[/SIZE][/FONT][/SIZE][FONT=Arial][SIZE=3], together with the -dev:

[SIZE=2]sudo apt-get install libgsl0ldbl
sudo apt-get install libgsl0-dev[/SIZE]

I think the trick might be that you have to specifically make an exception for any language that you don't want to include (aka don't have the packages for)
This is just my suspicion, if anyone knows exactly what just happened here, please go ahead and add it.
[/SIZE][/FONT]

---

### Post by srisatish on 2010-11-30
+ Ran into the same (after installing yacc/lex)
[INDENT] make[3]: Entering directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
 \
      \
 /bin/bash ../../ylwrap `test -f 'src/thriftl.ll' || echo './'`src/thriftl.ll .c thriftl.cc -- /bin/bash /home/kv/Downloads/thrift-0.2.0/missing --run flex 
 make[3]: *** [thriftl.cc] Error 1
 make[3]: Leaving directory `/home/kv/Downloads/thrift-0.2.0/compiler/cpp'
[/INDENT]
+ Rerunning 
 ./configure 
After installing bison and flex and make completed without any issues.

---

