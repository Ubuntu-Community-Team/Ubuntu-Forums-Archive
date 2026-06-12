---
title: "Privoxy and PS3 Help"
date: 2010-04-28
forum: General Help
---

### Post by HairyToeKnuckles on 2010-04-28
[SIZE=3]Hello everyone and thanks in advance.

Let me preface this topic by saying that I do not have much experience in Linux. I installed Ubuntu a few days ago looking for an alternative to Windows.

While I am loving Ubuntu, there are a few things I need to have work for me before I can use Ubuntu as my primary OS (currently dual-booting Ubuntu 10.04 and Windows XP).[/SIZE]

[SIZE=3]On my XP setup, I use Privoxy to act as a proxy server for my PS3 for the sole reason of speeding up downloads on PSN (demos, etc). Without using a proxy server, PSN is painfully slow for me (I think Comcast throttles it, or something).

What I need is someone to talk me through (like talking to a child discovering Ubuntu for the first time heh) how to go about installing Privoxy in Ubuntu and setting it up to use alongside my PS3 as a proxy server.

If it would be easier to use Squid or some other proxy, please explain that instead.

Once again, thanks for your help in advance.

Edit to add: I should point out that I have seen people explain how to setup Privoxy when wanting to download off of the PS3 using a direct url. What I want to do (if possible) is to setup Ubuntu to work with my PS3 as my Windows setup does whereas I just leave the XP machine running Privoxy in the background all the time while using the PS3. Basically, I just turn on Privoxy and just let it go.
[/SIZE]

---

### Post by bodhi.zazen on 2010-04-28
Privoxy in Linux is very similar to privoxy in Windows.

See if this post helps :

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

You might want to firewall that thing =)

Otherwise what step are you having a problem with ?

Last, as you are new here, please use the default font size. If you are having problems reading the site, adjust your browser. ( Ctrl + )

---

### Post by HairyToeKnuckles on 2010-04-28
While I am sure that link would provide ample help to those familiar with Ubuntu, it is too much for me to follow with my limited knowledge. I am still looking at it, however, and trying to make sense of it all.

I assume I am supposed to use the terminal under applications > accessories to enter the info you provided under that link. I was having trouble editing the file in the terminal (finding the line. Hitting Ctrl + W and typing listen-address returned nothing). I will keep playing with it and see if I can't get it to work, however.

Thank you.

Edit to add: Also, when I edited it an editor, when I went to save the changes it wouldn't let me save it with the same file name--which would defeat the whole purpose of editing the file. I know I am doing something ridiculously wrong.

---

### Post by bodhi.zazen on 2010-04-28
There is a bit of a learning curve with Linux, but privoxy is privoxy and most of the configuration of privioy is the same on both OS.

If you prefer a gui , use 

```
gksu gedit /etc/privoxy/conf
```

The rest of the links is iptables, and yes it is a tad complex, sorry about that, but it should be a one time set up and there is no graphical tool to do it for you.

---

