---
title: "Novell Client on Ubuntu"
date: 2006-02-17
forum: General Help
---

### Post by aggiechemist on 2006-02-17
Can anyone give me some help on getting the Novell Client to work on Ubuntu?

I know this is in a few other forums, but I can not find a clear or really helpful guide to getting it to work.

First of all, for anyone who doesn't know, the client I mean can be located here:
[http://download.novell.com/index.jsp?product_id=&search=Search&build_type=SDBuildBean&families=2586&date_range=&keywords=&x=26&y=16](http://download.novell.com/index.jsp?product_id=&search=Search&build_type=SDBuildBean&families=2586&date_range=&keywords=&x=26&y=16)

Novell has a little bit of documentation, though I haven't been able to learn much from it, here:
[http://www.novell.com/documentation/linux_client/index.html](http://www.novell.com/documentation/linux_client/index.html)

The problem is that most of the instructions are focused on Suse, Redhat packages, and YAst.

I downloaded it, pulled out the tarball, and installed with the following:
sudo alien -i /home/$user/Desktop/NCL_disk/*/*.rpm

or perhaps I made the folder more specific, but you get the point (I hope :)).

So here are some problems I have:
1. Where is the GUI? I can't seem to find a command or a Nautilus add in (or a KDE add in if I switch to that). I can't find a tray icon that I can run, or any such thing. I can find some programs installed, but they don't seem to do anything. Has anyone who installed this actually found a GUI interface at all???
2. I do have the ncp file system stuff installed (like mountncp). I can't figure out how to use it, but I have it. Yes I have looked at the man page, it wasn't clear to me how to use it though.
3. I need a remote server. As far as I can see in most of the other forums and the few guides I have found, everyone else has tried to work on a local server. I need to tell the thing an IP address and possibly a tree and a context and a username and password in order to connect. Browsing my local network just can't work for me.

Has anyone done anything like this? Or maybe there is a really nice how-to? I am happy to experiment or collaborate or give more details, but I'm lost for now.

Finally, since you might ask, my sys-admin is clueless. I asked him about it, and he suggested I try it and let him know how to do it if I have any luck.

---

### Post by aggiechemist on 2006-02-19
Bump. Yes, bumps are a little annoying but I'm still lost after a few more days of playing with this.

But I will give it a bump haiku:

Novell client pain
I don't like my sysadmnin
but love Ubuntu

---

### Post by aggiechemist on 2006-02-20
I just wanted to say I finally got it working. I managed to do it just using ncpfs using the command line. It took a lot of work, but I am thrilled I figured it out on my own.

I never did get the client working, but that is fine since I have a work around.

If someone else finds this thread someday becasue they are stuck, drop me a message or email or something and I will see if I can carry across what I learned.

---

