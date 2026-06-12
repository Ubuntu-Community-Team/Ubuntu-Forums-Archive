---
title: "Can't get opengl (libgl) working :("
date: 2010-03-23
forum: General Help
---

### Post by dinozzo on 2010-03-23
Hi, i'm hoping someone here can help me with an opengl error im getting. Im trying to compile an xbmc build using this [http://forum.xbmc.org/showpost.php?p=485944&postcount=7](http://forum.xbmc.org/showpost.php?p=485944&postcount=7) but when compiling I get this error:

checking for main in -lGL... no
configure: error: Could not find a required library. Please see the README for your platform.

Now, I have been told its opengl related and that the nvidia drivers provide libgl. I have tried uninstalling the nvidia drivers using envy and reinstalling them but the problem remains. Another suggestion was to check simlink:

ls -la /usr/lib/libGL.so

Which returned this:

lrwxrwxrwx 1 root root 27 2010-03-04 09:20 /usr/lib/libGL.so ->  /usr/lib/libGL.so.195.36.03

I have no idea what this means and what to make of it.
In /usr/lib/ there is a libGL.so.1 file but no libGL.so file

Is there a way to fix this problem or even removing everything nvidia/opengl related and starting again? I would like working opengl!

Any help would be very much welcome.
TIA

---

### Post by pbrane on 2010-03-23
/usr/lib/libGL.so is a link to the real nvidia ogl driver which is libGL.so.195.35.03 in your case. The linker will use whatever /usr/lib/libGL.so points to.

kali in the XBMC forum has provided a fix for you.
[B]fix:
ln -fs /usr/lib/libGL.so.195.36.15 /usr/lib/libGL.so [/B]
You'll need to use *sudo* in front of that.

It seems your symlink is wrong somehow. I have the same driver as you and the symlink is correct on mine.

---

### Post by dinozzo on 2010-03-23
I may have a fix. It seems a simlink was incorrect. the output of ls -la /usr/lib/libGL.so* is this:

root@ubuntu:~# ls -la /usr/lib/libGL.so*
lrwxrwxrwx 1 root root     27 2010-03-04 09:20 /usr/lib/libGL.so ->  /usr/lib/libGL.so.195.36.03
lrwxrwxrwx 1 root root     18 2010-03-23 18:56 /usr/lib/libGL.so.1 ->  libGL.so.195.36.15
-rw-r--r-- 1 root root 742880 2010-03-16 03:14  /usr/lib/libGL.so.195.36.15         

the first line was red.

I have been told to do this

ln -fs /usr/lib/libGL.so.195.36.15 /usr/lib/libGL.so

Im posting this as it might be of use to someone.

Oh, pbrane beat me to it! :)

---

### Post by SirKingChase on 2012-06-11
I had this exact problem trying to compile for Eden,
Line was red and I corrected it the same way
 
sudo ln -fs /usr/lib/libGL.so.295.53 /usr/lib/libGL.so


 I guess what happens is there is an old driver that never gets moved back when you upgrade Nvidia drivers?

---

