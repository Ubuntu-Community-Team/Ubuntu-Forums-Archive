---
title: "Ubuntu 10.04 zlib installation with RVM issue"
date: 2011-11-28
forum: General Help
---

### Post by Lavix on 2011-11-28
I installed RVM on Ubuntu 10.04, then Ruby 1.9.2. and all the needed gems. The proble is that Ruby can't load 'zlib' package.
```

a187589@ubuntu:~/rails_projects$ cd blog/
a187589@ubuntu:~/rails_projects/blog$ rake db:create
rake aborted!
/lib/libz.so.1: version `ZLIB_1.2.3.3' not found (required by /home/a187589/.rvm/rubies/ruby-1.9.2-p290/lib/ruby/1.9.1/i686-linux/zlib.so) - /home/a187589/.rvm/rubies/ruby-1.9.2-p290/lib/ruby/1.9.1/i686-linux/zlib.so

```I have alreade tried a solution proposed on the RVM site [http://beginrescueend.com/packages/zlib/:](http://beginrescueend.com/packages/zlib/:)
```


$ rvm pkg install zlib
$ rvm remove 1.9.2
$ rvm install 1.9.2 --with-zlib-dir=$rvm_path/usr

```The only doubts I have is what I had to put instead of '$rvm_path/usr' ?
When I require 'zlib' in irb:
```

a187589@ubuntu:~/rails_projects/blog$ irb
1.9.2-p290 :001 > require 'zlib'
 => true 
1.9.2-p290 :002 > 

```everything seems to be OK. 

Here is the full stack trace:
```

a187589@ubuntu:~/rails_projects/blog$ rvm remove 1.9.2
Removing /home/a187589/.rvm/src/ruby-1.9.2-p290...
Removing default ruby interpreter
Removing /home/a187589/.rvm/rubies/ruby-1.9.2-p290...
Removing ruby-1.9.2-p290 aliases...
Removing ruby-1.9.2-p290 wrappers...
Removing ruby-1.9.2-p290 environments...
Removing ruby-1.9.2-p290 binaries...
a187589@ubuntu:~/rails_projects/blog$ rvm pkg install zlib
Fetching zlib-1.2.5.tar.gz to /home/a187589/.rvm/archives
Extracting zlib-1.2.5.tar.gz to /home/a187589/.rvm/src
Configuring zlib in /home/a187589/.rvm/src/zlib-1.2.5.
Compiling zlib in /home/a187589/.rvm/src/zlib-1.2.5.
Installing zlib to /home/a187589/.rvm/usr
a187589@ubuntu:~/rails_projects/blog$ rvm install 1.9.2 --with-zlib-dir=/home/a187589/.rvm/usr
Installing Ruby from source to: /home/a187589/.rvm/rubies/ruby-1.9.2-p290, this may take a while depending on your cpu(s)...

ruby-1.9.2-p290 - #fetching 
ruby-1.9.2-p290 - #extracting ruby-1.9.2-p290 to /home/a187589/.rvm/src/ruby-1.9.2-p290
ruby-1.9.2-p290 - #extracted to /home/a187589/.rvm/src/ruby-1.9.2-p290
Fetching yaml-0.1.4.tar.gz to /home/a187589/.rvm/archives
Extracting yaml-0.1.4.tar.gz to /home/a187589/.rvm/src
Prepare yaml in /home/a187589/.rvm/src/yaml-0.1.4.
Configuring yaml in /home/a187589/.rvm/src/yaml-0.1.4.
Compiling yaml in /home/a187589/.rvm/src/yaml-0.1.4.
Installing yaml to /home/a187589/.rvm/usr
ruby-1.9.2-p290 - #configuring 
...
the rest is omitted for easier reading


```So what is the problem, can anyone help me, please?
Thanks.

---

### Post by Lavix on 2011-11-28
Fixed. I think I forgot the dollar sign just before the path to zlib folder in the line:
```

$ rvm install 1.9.2 --with-zlib-dir=$/home/a187589/.rvm/usr

```

---

