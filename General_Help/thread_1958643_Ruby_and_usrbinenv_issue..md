---
title: "Ruby and /usr/bin/env issue."
date: 2012-04-14
forum: General Help
---

### Post by zozza on 2012-04-14
Hi, 

I have the following errors:

usr/bin/env: ruby: No such file or directory
/bin/sh: ruby: not found

which ruby reveals:

/home/homedir/.rvm/rubies/ruby-1.9.3-p125/bin/ruby

The /usr/bin/env file reveals:

GEM_HOME=/home/homedir/.rvm/gems/ruby-1.9.3-p125
IRBRC=/home/homedir/.rvm/rubies/ruby-1.9.3-p125/.irbrc
MY_RUBY_HOME=/home/homedir/.rvm/rubies/ruby-1.9.3-p125
PATH=/home/homedir/.rvm/gems/ruby-1.9.3-p125/bin:/home/homedir/.rvm/gems/ruby-1.9.3-p125@global/bin:/home/homedir/.rvm/rubies/ruby-1.9.3-p125/bin:/home/homedir/.rvm/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/homedir/.rvm/bin
GEM_PATH=/home/homedir/.rvm/gems/ruby-1.9.3-p125:/home/homedir/.rvm/gems/ruby-1.9.3-p125@global
RUBY_VERSION=ruby-1.9.3-p125

I would assume that this means Ruby is in env but apparently not. 

How can I resolve this error?

Thanks.

---

### Post by gordintoronto on 2012-04-14
Please, back up a step. You got the errors when you did what? Did you install something, if so what and how?

---

### Post by d3v1150m471c on 2012-04-14
```

'usr/bin/env ruby' != '/usr/bin/env ruby'

```
...
```

which env
which ruby

```

---

