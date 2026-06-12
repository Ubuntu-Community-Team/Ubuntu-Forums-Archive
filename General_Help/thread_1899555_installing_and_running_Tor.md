---
title: "installing and running Tor"
date: 2011-12-23
forum: General Help
---

### Post by gobotsoup on 2011-12-23
Hi I am trying to install Tor on Ubuntu 10.04. I was following the directions from [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)

I did all the steps and everything seemed to install normally. Then when I get to the step where I run the below command:
```
ss -aln | grep 9050
```

I am not getting the expected output, instead I am seeing the following:
```
0      128                    127.0.0.1:9050
```

Also when I go to the check.torproject webpage it says "Sorry. You are not using Tor".

Any suggestions on what I may be missing here?

---

### Post by boast on 2011-12-23
i assume you are using firefox with torbutton installed and enabled?

---

### Post by gobotsoup on 2011-12-24
> **boast said:**
> i assume you are using firefox with torbutton installed and enabled?

No, I haven't gotten that far yet. I am just trying to get tor running correctly. I have already installed tor and polipo, but when I run via the below commands:

sudo /etc/init.d/tor start
sudo /etc/init.d/polipo start

I get the following output:

Starting tor daemon: tor...
done.
Starting polipo: /usr/bin/polipo already running -- doing nothing
polipo.


Tor doesn't seem to be running though as I have explained in my previous post.

---

### Post by ottosykora on 2011-12-24
I have done the manual installation few times, it was always kind of try and error ops.
Did you get the polipo config from the torproject.org website?
This can make it more easy.

But you say that you were going to the test site of torproject...!! 
With what? With the firefox? In such case you have to switch it on by the torbutton extension first, otherwise there will be no tor use by the firefox.

However:
in the more recent installs of ubuntu, I simply installed tor and vidalia GUI from the repository and all was ok.
There is small problem:
when using vidalia, it attempts to start tor and polipo, but as default this is already running!
But it not connected to the tor network.
Vidalia returns error msg then.

there is some procedure described somewhere, but try this:

sudo apt-get install sysv-rc-conf

then run it
sudo sysv-rc-conf

in the table you see, scroll down by the use of arrow key to the line with tor and disable all ticks by the use of space key.
Leave the sysv-rc-conf with q.

Reboot and use vidalia to start  tor and connect to tor. For the firefox you need the extension torbutton.



New version:
the latest version of tor seems to include the whole proxy mechanism, no more polipo or privoxy installation needed. 
The latest update of tor seems to have also changed few things, this is also why it is neede to start the computer with tor stopped and start it with vidalia (well or other way).

---

### Post by haqking on 2011-12-24
Follow this

[https://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/](https://dangertux.wordpress.com/tutorials/tor-polipo-5-minute-install-guide-ubuntu-11-0411-10/)

And your output shows tor as running, and to for the tor website to show it as working, you need to make your proxy as your local machine like 127.0.0.1:9050 or use the browser tor addon

---

### Post by ottosykora on 2011-12-24
I have alos just seen they have the tor browser bundle also for linux now.

I think this is the best solution, as there is most of the things tested and dangerous parts not contained.

Try it, works fine. No complex installation, works out of the box.

[https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)

---

### Post by haqking on 2011-12-24
> **ottosykora said:**
> I have alos just seen they have the tor browser bundle also for linux now.

I think this is the best solution, as there is most of the things tested and dangerous parts not contained.

Try it, works fine. No complex installation, works out of the box.

[https://www.torproject.org/download/download-easy.html.en](https://www.torproject.org/download/download-easy.html.en)

Though that is true, to the OP remember that only applies to web browsing.

If you wish to take advantage of TOR for IM or IRC then you need it installed and running locally with something like privoxy or polipo.

Anyways as i said above, your first post shows TOR as running so no problems, you just need to configure whatever app you wish to use it by placing the proxy information which would be 127.0.0.1:9050

---

### Post by ottosykora on 2011-12-24
the latest versions do not need polipo or privoxy any more and can be configured for generic soks.
The update made kind of mess of it, but then I noticed the changes. It was apparently released abt a week ago.
The proxy is apparently included i nthe tor and it works also with TB if configured properly for example.

---

