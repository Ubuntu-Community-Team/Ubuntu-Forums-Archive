---
title: "Need help for Sudoers editing"
date: 2011-08-22
forum: General Help
---

### Post by RakanN on 2011-08-22
Hello,

I'm trying to allow a specific group on my machine to execute one command with sudo without requiring a password, so what I want to do is add something like this to sudoers: 

%groupName ALL = (ALL) NOPASSWD: /bin/bash /path/to/shfile.sh argument1 argument2

argument1 needs to be a url : [http://subdomain1.subdomain2.domain.com](http://subdomain1.subdomain2.domain.com) 

argument2 needs to be a path of the form /var/www/demo/**SomeFolder**/application/config/config.php

How do I put in a regex form that sudoers will understand ?
I tried reading the sudoers manual, but it didn't help a lot .

Any help would be very much appreciated.
Thank you .

---

### Post by kartabosh on 2011-08-22
i'd say to leave sudoers out of that 

%groupName ALL = (ALL) NOPASSWD: /path/to/script.sh

script.sh should worry about the arguments 
it can't be that hard to do it in bash, unfortunately i'm no good at bash

---

