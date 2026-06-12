---
title: "Reference implementation for daemon scripts?"
date: 2009-10-29
forum: General Help
---

### Post by nodje on 2009-10-29
I'm still pretty new to Linux, and I'd like to know the PROPER way to create startup scripts.
There's many resources around on the web, but too many actually, and this is confusing.

/etc/init.d/skeleton seems to be the definitive good way to proceed.

I'm wondering though if there is cases when one should not use this script? 
Are there cases where you would rather not have your process run as system daemon?

As far as I'm concerned, I want to run a couple of things including Subversion and Tomcat.
Is copying skeleton the right way to go?

If so, as I understand, replacing variable values is the only necessary step.
I'm a beginner in scripting, but it seems that the whole script - besides var affectation - should belong to another file since it never changes. 
How can I do that? Is it easy to call a part of a script from another file?

~nodje

---

### Post by nodje on 2009-10-30
:( 
to /etc/init.d/skeleton or not to /etc/init.d/skeleton ?
that is my question ...

---

### Post by Anthon on 2009-10-30
If you are planning on going to Ubuntu 9.10 anytime soon, you should be looking at upstart ( [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) ). It replaces all this /etc/init.d/ stuff.

If you are stuck with pre 9.10 versions for a while and given that /sbin/init will  it is probably not so important to have the perfect script.

In my experience the differences between distros ( SuSE, RedHat and Ubuntu is what I used to maintain) make it difficult to have generic script. It also accounts for the different 'recipes' out there.

---

### Post by nodje on 2009-10-30
thanks for links Anthon.

I actually just did the upgrade to 9.10 - that ran flawlessly over an ssh connection, it's beautiful.
And I just coded the script based on skeleton. 
But anyway, I'll have a look at upstart, that looks nice.

Out of curiosity, since I'm starting to code script on Ubuntu, is it possible to put a script part that would be common to many scripts in a separate file, like you do when you code in C or Java?

---

### Post by Anthon on 2009-10-30
> **nodje said:**
> thanks for links Anthon.

I actually just did the upgrade to 9.10 - that ran flawlessly over an ssh connection, it's beautiful.
And I just coded the script based on skeleton. 
But anyway, I'll have a look at upstart, that looks nice.

Out of curiosity, since I'm starting to code script on Ubuntu, is it possible to put a script part that would be common to many scripts in a separate file, like you do when you code in C or Java?

I am not running upstart myself yet. Going to have to wait until I am back from travelling to try 9.10 out. I am not sure how the replacement for /etc/init.d/ is implemented in 9.10, but AFAIK upstart allows you generate events through the DBUS facility so any (scripting) language supporting that and inclusion of common scripting would help you.
For (ba)sh scripts that is done with lines like:
. /lib/lsb/init-functions

---

