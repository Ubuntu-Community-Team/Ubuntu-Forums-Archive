---
title: "sudo password problems"
date: 2011-11-11
forum: General Help
---

### Post by MetapostAddict on 2011-11-11
Hi all,

For some reason my sudo password isn't working, even though I haven't changed the password.  I tried to log into recovery mode and into root to change my password, but I get the error message "authentication token manipulation error," and I can't change the password.

I've checked the dumb stuff, like caps lock etc.  

Any ideas??

Thanks.

---

### Post by pr3zident on 2011-11-11
> **MetapostAddict said:**
> Hi all,

For some reason my sudo password isn't working, even though I haven't changed the password.  I tried to log into recovery mode and into root to change my password, but I get the error message "authentication token manipulation error," and I can't change the password.

I've checked the dumb stuff, like caps lock etc.  

Any ideas??

Thanks.

sounds weird 
did you do passwd root or your username ?

---

### Post by MetapostAddict on 2011-11-11
> **pr3zident said:**
> sounds weird 
did you do passwd root or your username ?

from the root prompt I just typed "passwd" then when prompted I entered a password, then again, then I received the error.  I also tried "passwd user" where user is my regular user name.  I don't think I tried "passwd root"

---

### Post by raja.genupula on 2011-11-11
Reset your password from here 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by MetapostAddict on 2011-11-11
> **raja.genupula said:**
> Reset your password from here 

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

yes that's exactly where I got the info I used to do what I describe above.  I logged into recovery mode, reached the root prompt, but when I try to change the password I get the authentication token error.

I should be more clear about what I did:
I log into recovery mode using the instructions above.  
I select the "Drop to root" option
From root prompt, I type "passwd root"
I enter my password twice.
I get the error message Authentication token manipulation error

---

### Post by MetapostAddict on 2011-11-11
> **MetapostAddict said:**
> yes that's exactly where I got the info I used to do what I describe above.  I logged into recovery mode, reached the root prompt, but when I try to change the password I get the authentication token error.

I should be more clear about what I did:
I log into recovery mode using the instructions above.  
I select the "Drop to root" option
From root prompt, I type "passwd root"
I enter my password twice.
I get the error message Authentication token manipulation error

I'll try the emergency password reset now...

---

### Post by raja.genupula on 2011-11-11
> **MetapostAddict said:**
> I'll try the emergency password reset now...

May be this can help you ...2nd solution 
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

---

### Post by MetapostAddict on 2011-11-11
> **raja.genupula said:**
> May be this can help you ...2nd solution 
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)

the emergency reset, i.e., booting from live cd to manually edit the shadow file, worked.  Thanks for the help.

---

### Post by MetapostAddict on 2011-11-11
curses: double post.  Mea Culpa.

---

### Post by BillyBoa on 2011-11-11
> **MetapostAddict said:**
> the emergency reset, i.e., booting from live cd to manually edit the shadow file, worked.  Thanks for the help.

Please note the thread as SOLVED from the Thread Tools

---

