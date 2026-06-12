---
title: "ZoneMinder in Ubuntu 9.10: Where's the web GUI?"
date: 2010-01-12
forum: General Help
---

### Post by MaxBrains on 2010-01-12
I was hoping to have a computer-based system to monitor some security cameras I've been planning to install as a result of a specific security issue at my house. For this purpose, I chose ZoneMinder.

Since I've used Kubuntu on a desktop system before, I chose to use Ubuntu 9.10 server edition to run ZoneMinder. I installed it along with LAMP and the OpenSSH server. I then upgraded all the existing packages, configured the network interface to use a static IP (192.168.1.200), installed nullmailer on its own from the repository (as suggested by a blog post here: [http://www.rickwargo.com/2009/12/28/installing-zoneminder-1-24-1-on-ubuntu-9-10/](http://www.rickwargo.com/2009/12/28/installing-zoneminder-1-24-1-on-ubuntu-9-10/)) and, finally, installed ZoneMinder from the repository. All of this came through without any errors that I could see.

The problem: **I can't find the web GUI.** Wherever URL it's supposed to use is, strangely, mostly absent from the ZoneMinder documentation that exists. What sources I've found say that it's supposed to be accessed at [http://192.168.1.200/zm](http://192.168.1.200/zm) , but when I try that, the Apache server throws a 404. I also tried [http://192.168.1.200/zoneminder](http://192.168.1.200/zoneminder) and got the same error. Incidentally, [http://192.168.1.200/](http://192.168.1.200/) on its own gives me Apache's default page, which, I assume, just means that's working properly.

I can think of three reasons for this:
[LIST]
[*]For some reason, the Ubuntu release of ZoneMinder is configured to put the web GUI on a different URL.
[*]The installation process did not install the web GUI, either because I didn't specify it, or because of an unseen error.
[*]There's something else that's fundamental to this process which I have not been told about.
[/LIST]

As I said, I've used mostly desktop systems. I have a very basic understanding of using a shell and know very little about how Linux and web servers work on the inside.

Any good leads on where the web GUI is, or at least where I can find out, would be much appreciated.

---

### Post by MaxBrains on 2010-01-12
After some research (reading /usr/share/doc/zoneminder/README.Debian!) I learned what I needed to do. Whoops. After some discussion by IRC, I did:
```
sudo ln -s /etc/zm/apache.conf /etc/apache2/conf.d/zoneminder.conf
```
and then:
```
sudo /etc/init.d/apache2 reload
```
And the web GUI started working.

It seems silly that this wasn't done for me, but I'm glad that this solved my problem. As they say, RTFM, I guess.

---

### Post by santhony on 2010-01-13
Great Post... this helped me out!

Thanks for Posting!!

---

### Post by the_genrl on 2010-03-25
hey there this helped me out as well!  thank you!

---

### Post by ephestione on 2011-03-31
You really should mark is as solved, and change the thread title to make it clear it's not a question but a how-to ;)
Anyway thank you for the info, helpful in my case as well ;)

---

### Post by xalu on 2011-04-05
I had this same exact issue, however, after trying the above command nothing is fixed. 

I am getting a 403, permission denied.

running 10.10 server edition

---

