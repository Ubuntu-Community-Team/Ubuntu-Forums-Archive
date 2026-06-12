---
title: "can u provide some insight on this crash dump?"
date: 2012-07-27
forum: General Help
---

### Post by asdfA on 2012-07-27
Hello - I have downloaded Riak source to my Ubuntu instance.  When I execute "make devrel" from the terminal erlang writes out an error to the terminal and logs the error and crash dump to erl_crash.dump:

make: git: Command not found
mkdir -p dev
(cd rel && ../rebar generate target_dir=../dev/dev1 overlay_vars=vars/dev1_vars.config)
==> rel (generate)
{"init terminating in do_boot","Release riak uses non existing application os_mon"}

This is my first time to debug an erlang stack dump.  I googled the error but didn't find any good answers off hand.  Please help :)

---

### Post by ubudog on 2012-07-27
Hi there!

From "make: git: Command not found", it seems git is not installed.  Try this:
```
sudo apt-get install git
```

---

### Post by asdfA on 2012-07-27
hi ubudog - thanks for the quick response! I did the install you recommended and now erlang reports the following error:

Slogan: init terminating in do_boot (Release riak uses non existing application os_mon)

Any idea on the root cause of this error?

---

### Post by ubudog on 2012-07-27
Try installing this package:
```
sudo apt-get install erlang-os-mon
```

Best of luck!

---

