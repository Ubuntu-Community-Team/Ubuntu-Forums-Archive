---
title: "problem with apache2 not displaying site properly"
date: 2009-11-24
forum: General Help
---

### Post by bobonthenet on 2009-11-24
I am using Ubuntu 9.04 with apache2 I have 3 sites hosted that look fine.  I just tried to set up a 4th site which is simply a wordpress blog.  It seems that on this 4th site none of the CSS works when viewed remotely.  If you go to the site from the LAN it looks fine.  It only looks messed up if you actually go to the website outside of the LAN.  I configured my sites-available and sites-enabled by copying and pasting from one of the 3 sites that do work and then using a find and replace to change the parts that needed changing.  What did I forget to do this time?  I know I must have probably forgotten something simple but I can't figure it out or remember what I'm missing.

---

### Post by bodhi.zazen on 2009-11-24
You are having problems because you configured Wordpress with your local ip address. 

Your local (private) ip is available on your lan, but not outside your lan ...

On your WP admin panel, what is entered in your Site URL and the Blog URL ?

Change them from "localhost" or "127.0.0.1" or your lan IP to your public url / ip.

---

### Post by bobonthenet on 2009-11-24
Thanks that was definitely the problem.  I was totally off base and definitely thought it was a server issue and not with wordpress itself.

OK new problem and I know this isn't really the place to ask since this is a wordpress problem but I figure you probably know the answer.  I'm having the same problem in reverse.  I can't view the site properly on the LAN but it looks fine remotely.  My wife is really upset with me I appreciate your timely response.

---

### Post by bodhi.zazen on 2009-11-24
LOL

Well, how many boxes do you have on your LAN ?

Start by clearing your cache.

The next option is to check your host file and point your WP requests to your LAN.

Is your server in a DMZ ?

---

### Post by bobonthenet on 2009-11-24
Well now I've locked myself out from both ends!  I've set up other CMS and never had this much trouble.  I've got 4 boxes on my LAN right now including the server.  Usually when going to one of my websites from home I go [http://localip/sitename](http://localip/sitename) and then remotely it is just [http://sitename.com](http://sitename.com) I expected the same thing of wordpress.  Do you happen to know which file contains the URLs so I can manually edit them back to where I can get back on the site, then from there I'll work on figuring out how to get my host file right.  I never expected this to be such a big job, isn't wordpress supposed to be one of the easier CMSes?

---

