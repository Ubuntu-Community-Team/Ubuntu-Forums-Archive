---
title: "All-In-One Server"
date: 2012-04-06
forum: General Help
---

### Post by DutchShrek on 2012-04-06
Hi all

I am trying to setup a server for home use. Though I'm not entirely sure what to use. Since Ubuntu is among the most supported I figured I'd give it a shot here.

The problem I encounter is not a lack of tutorials, it is more organization. I am not sure where to start and where to proceed.
So I was hoping someone here could point me to a tutorial (or set of tutorials) that cover what I wish to accomplish.
I am going to assume that Ubuntu Server 10.04 LTS would be a good base?

What I hope to aim for basically is:
-Headless (I like my dual screen setup on windows and only have 2 screens :) )
-A Web server (serving a web site or two to my family overseas to share a photo gallery and stream home videos)
-File sharing within the home network (1 PC and 4 laptops) -->webdav?
-Streaming to my Xbox360. 
--This is the biggest one. I know there are a lot of options but I have no idea what the best one is (I know, objective)
But while looking I'm also trying to find out if on-the-fly transcoding is possible as I have some mkv files that the xbox can not play.
I can use my Windows machine for this with tversity but I'd like to move my files over to the server.


optional;
-File sharing outside the home network (Android based phones as well as with family overseas (though I suppose the latter could be done easily with dropbox)
-sharing an (outlook) address book

I will point a subdomain to the server as well as subdomains to the gallery/video site.

If anyone has any more suggestions on what to do with this server I would appreciate hearing them.

Oh, the hardware is actually pretty good.
No video card, but it does have a core2duo and can easily run windows 7. Only 2gigs of ram, but should be sufficient for what I wish to accomplish (i hope)


I'm sure plenty of people have done what I want to do, I'm merely hoping to find out exactly how they did it.
The thing I have to point out is that I am a Linux n00b...no seriously I have come back to ubuntu at least 4 times only to fail and give up every time.
I should probably just stick to windows, but I don't want to use windows for this and I know for a fact that it can be accomplished.


ps; I tried Amahi, but the streaming video didn't work out. The apps I found cost money.
And if I have to install manually I might as well get rid of the bulk I don't need. Start from scratch.

---

### Post by zero2xiii on 2012-04-06
Hay, 

I can help you with some of those.. Not all of them (like the streaming part I haven't done before.)


So lets start at the top. I will rather type out the process than point you to numerous tutorials, since I have some preferences I would recommend you consider as we go along.

---

### Post by zero2xiii on 2012-04-06
> **DutchShrek said:**
> 
-Headless (I like my dual screen setup on windows and only have 2 screens :) )


Lets start here, it will be easier (for setup) to have a screen. You can later setup the system to boot to a non gui environment. But editing files and all that is a hassel (for me personaly) using terminal apps such as nano and the likes.

> -A Web server (serving a web site or two to my family overseas to share a photo gallery and stream home videos)

Setting up a webserver is pretty easy. Managing the website itself is harder, esp setting up streaming (thinking youtube). But heres how to get it going: (I will try to make the steps clear enough to follow even over ssh)

```
sudo apt-get install apache2
```

you are done installing apache.
Setting it up is way more complicated, I like using webmin:
[http://www.webmin.com](http://www.webmin.com)

```
wget http://tenet.dl.sourceforge.net/project/webadmin/webmin/1.580/webmin_1.580_all.deb #downloads package file
sudo dpkg -i webmin_1.580_all.deb #installs package
```

btw to access webmin:
[https://127.0.0.1:10000/](https://127.0.0.1:10000/)
Then accept the security certificate. And then login with a user name and password with sudo rights (preferably the same user you will use to setup everything). Webmin also support samba shares, so this will be awsome. You can also access webmin from any computer that has access to your computer by pointing it to http**s**://ip_to_webmin_computer:10000 We can also forward this port later to the internet so you can access the page from anywhere in the world. Useful, but obviously there is a big risk involved in doing it.

Oka I know I said I wont point to tutorials, but look at these for your liking of how you wish to configure apache:
Multiple Websites on one server: [http://rimuhosting.com/howto/virtualhosting.jsp](http://rimuhosting.com/howto/virtualhosting.jsp)

You can also use that to configure just one website, just note how many users are created and such. I do recommend creating a different user, with restricted acount, for the server files. Thus reducing the security risks involved by the server.

Now add the files to where you created the directory for the server. The server should now be accessable by the network. navigating to [http://localhost.com](http://localhost.com) should give you either the "it works" page, or the webpage you put there. Making this availible to the internet we will cover later. Since we need to forward a few ports for all the things you want to share over the internet, we can do them all at the same time.

> -File sharing within the home network (1 PC and 4 laptops) -->webdav?

Not needed. Just samba? If you want an FTP server running, we can do that aswell.

SAMBA:
```
sudo apt-get install samba
```
 and you are done. To share a folder, rightclick and select sharing options and select as needed. For terminal assistance, or more detailed setup see: [https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

Do you want to set-up an ftp server?

Oka I think we should stop here first. If you followed up to here, then samba and apache should be working.

---

### Post by DutchShrek on 2012-04-06
Wow first off, thanks
I appreciate you taking the time to write that, really

Ok so I guess you did not have Ubuntu server in mind since it does not seem to have a gui.
If I may ask, which version would you recommend? Simply the latest one? 11.10 or 10.04 LTS?

---

### Post by gordintoronto on 2012-04-06
My two cents: you might find that your ISP does not allow you to run a web server. There are photo and video sharing sites, and they work very well. For example, you can put videos on Youtube which can only be watched by people who have the address.

Ubuntu desktop does file sharing just fine; it's really simple. Right-click on a folder, select share it, check all the boxes. The first time you do it, you might be prompted to install Samba.

Like zero2, I suggest having a monitor attached for the initial setup, then get SSH running, or VNC if security inside your LAN is not a concern.

Ubuntu 12.04 will be released in three weeks, and will be supported for five years. The Release Candidate should be available sooner, and updates will make it the same as the final product. That is not true with the beta, which is currently available.

For streaming, I know the acronym DLNA, but that's the end of my knowledge. Perhaps the Xbox supports it.

---

### Post by DutchShrek on 2012-04-07
you're right, but youtube still has it's limits because of that.
The fact that I need to give my family a link to each and every video is bothersome to say the least.
And I've tried scripts like phpmotion,clip-bucket and cumulus clips
None of which work on my web host. (crocweb)
Sure, I could switch hosts, but I've already paid for the year.

The photo gallery can easily be done online, last I checked I should be able to get gallery3 working on any web host.

But those videos.
I don't know it just seemed extremely tiresome to upload at youtube, take the embed code and place in my own script for display.
Scripts like phpmotion were made for a reason, I like to think I fall into that category.
I don't have a big family, and I don't think I'll be uploading that much more than what I do now. I'm not sure if my bandwidth would raise flags at my ISP. Could be wrong though, and it's something to think about.
But I still want easy access to my files from anywhere I see fit through a browser. So even if I do not stream video from home I still need to have the web server up for easy access.
Trust me, my mother is not one to use ftp.


But, from a server I would imagine that if it remains headless it would use less resources. Am I wrong in assuming this? Is that not why there is a separate server edition?
And for streaming to the xbox I would imagine that a GUI desktop would make things slow down a bit.
I don't know, I'm not an expert, I'm quite the noob. These things just seem logical to me. Please correct me if I'm wrong.

---

### Post by jadtech on 2012-04-07
your ISP will pick up on something like web servers and mail very quick, you think the use will be the same but the server runs 24/7 open to any and all at the same time your still doing everything you normally do each day on the service ...

if the issues is videos using youtube and needing to share many addresses to them try a site like shutterfly which is free  host for pictures and video ..

---

### Post by clickwir on 2012-04-07
Just a quick 2 cents. 

I'd go with 12.04LTS, I know it's Beta right now. But it's pretty close to final. It's a LTS, so it's more conservative than a normal release. And in less than a month it will be final. Most things are frozen by now anyway, it's just bug fixes really. Generally, there's not going to be major version changes or anything that would break things.

With that said, whenever I look for help. I start at Google and limit my search to things within the past year. (Left sidebar, More Search Tools, Past Year) That really helps weed out a lot of older tutorials/howtos that are out of date.

However, if you go with a 10.xLTS, that won't help as much. But still, I would limit search to a time frame. I've been burned by reading half way through a tutorial, only to find it was from 2008 and everything after that point is different.

Also, Webmin is a great tool for simple remote server management.

Now, with that said; you need to consider what browser/device/platform your users (family) will be using. If that's set in stone and never going to change, fine, you can set things up, get it working and be done. If they change to something else, get a smartphone and still want to see your videos... well that means more work for you. *OR* you could just upload them to youtube, mark them as private and just email the people the links. That takes a lot of hassle now and in the future, off of you. Oh, and most home internet connections are not well suited for streaming video. Ok, maybe one. But what if 2 or more people want to view it at any one time, they are going to have to sit and wait. That's less and less acceptable with sites like Youtube that are designed for this.

Don't get me wrong, I'm all for learning and setting up things to test and gain knowledge. Just remember to try and understand your, your ISP, and your setups limitations and who your customers are.

---

### Post by DutchShrek on 2012-04-07
Ok so let's for argument sake say I find a means that will be better than youtube, or I find a great way to use the youtube videos on a site that actually runs on my host.
Lol that means anything but a youtube clone script like I hhad in mind.

It sounds like I need samba for lan fileshare. Sounds simple enough.

So that's 2 down, still 1 to go.
The streaming to xbox thing...is anyone using something that actually works?
Preferably with on the fly transcoding like tversity does?
I saw something called plex but haven't had time to read much on it yet. You guys tried it? It looks like it streams to smartphones too, kinda cool if it does.
Xbmc I think it goes for avi and such. But no transcoding so no mkv.

I have to say I do appreciate the advice so far guys.
I am going to start from scratch with 12 and try to make things work as best I can.
Hope to hear more

---

### Post by zero2xiii on 2012-04-07
Hay,

Oka I got lost now what everything is you are going to run on your server.

I have no real knowledge concerning streaming so I wont be able to assist you with that, maybe someone else will be.

You still need port fowarding to happen to access ANYTHING from outside your local network. See: [http://portforward.com/](http://portforward.com/) for details ons forwarding ports on your specific router.

You need to forward the following for specific services:

FTP: 21
HTTP: 80 or 8080 or 8008 ->> this is dependant on how you setup apache, the default is port 80, but most routers's config page is also on this port and it may cause issues, so I suggest changing it. Remember, those port numbers aren't set in stone. You can change them (just make sure to change everything to that port, all the config files) and then just forward your ports correctly according to the non standard setup
webmin: 10000

Please try and use non standard ports outside, for example FTP traffic might be re-routed as such:

Internet > some.domain.ext**:741** > router port 741 > local server port 21.

Thus connecting to the ftp server (only as an example) will be acomplished by typing [ftp://some.domain.ext:741](ftp://some.domain.ext:741) Thus throwing off drive by port scanners picking up on the ftp server running.. Just an added bit of security from script kiddies... Also I recommend you register at an free dns server to get a domain name for your IP (either dynamic or static). I personaly use dyndns.org. There is a guide on setting up software to track a dynamic IP to them so you can always use the same domain name to access your server no matter the IP change the server might undergo.

Any questions, just shout. I to will be upgrading to ubuntu 12.04 when it comes out. As far as the performance from a GUI to Non-GUI system goes. There is so little difference (on my systems atleast) that I dont think it is much of a trade off. And you can always disable a graphical boot by:

```
sudo update-rc.d -f gdm remove
```
and to get xorg running (should you want or need it)
```
startx
```
to get things back to normal
```
sudo update-rc.d -f gdm defaults
```

This will just disable the graphical system, saving those resources if you REALLY feel the need :)

Cherz

---

### Post by DutchShrek on 2012-04-07
No no I still have every intention of following your suggestions because the web server allows me to have a nice local testing platform for web sites. Whther or not I make it accessible to the outside is still on my mind but not a priority.

I simply have no time this weekend but hopefully I can work on it a bit throughout the week.
The remote connection thing is kind of big thouggh and vnc is incredibly slow. I intend to use ssh as much as possible.
This is not only because of the screen. Its also because my desk is not big enough to setup 2 kb/m sets. So the more I can use my main computer the better.

Anyway, I installed the 12 beta and samba is installed. I will be sharing the folders with the local computers using that.
Perhaps tomorrow or Monday I will follow your suggestions provided so far and keep you posted on my progress.

I happen to have a static ip and added an a record server.mydomain.com at my host.
Also, I'm not sure dyndns is still free. It didn't look like that when I last saw. Could be wrong though.
I never thought of using a different source port while forwarding. Great tip, thank you!


Thanks

---

### Post by zero2xiii on 2012-04-07
> I happen to have a static ip and added an a record server.mydomain.com at my host.

This is awsome! That means you don't need to worry about the dns setup part. You might just aswell point them directly to the IP... Saves some hops and reduces latency sometimes..

> I never thought of using a different source port while forwarding. Great tip, thank you!

Only a pleasure! I learned this nifty trick after some ports were blocked by my ISP for some servers I run. (nothing normal hahaha... Stuff such as Trunked Radio Systems and IP based radio, think Echolink)

Anyhow, I have subscribed to this thread so Ill keep an eye out :).

SSH is a great way to work. Remember the -Y flag to forward xorg. Thus you can run graphical programs localy, on the other pc. This is not IDEAL, and not NEARLY as good as VNC and all that, but it does work :guitar:  EDIT: I am not sure if this works on a windows computer, as I use this between 2 ubuntu computers, server running 10.04_64 Ubuntu and several different clients ranging from 9.04 (yep) to 11.10... 

Any way.. Cherz

---

### Post by gordintoronto on 2012-04-07
As a comment, I have installed Apache, MySQL and PHP on my Ubuntu *desktop* system in order to test web site development, and it all works just fine.

Once you have SSH running, you can put the computer anywhere, it doesn't have to take up desk space.

---

### Post by DutchShrek on 2012-04-17
I keep running out of time and with the summer being this close I imagine I will have even less time to properly set everything up the way I want it.
So since my Windows PC can stream to xbox and the other can keep my files I can be happy for now.
But I have to leave it at that.

So zero2xiii I wanted to at least post and show my gratitude for your attempt at helping me.
Trust me, if I had the time I would be following your steps to the letter. 

Anyway, thanks a lot for trying to help me. Thanks to the rest of you to share your suggestions. I appreciate the help I got, regardless of not being able to utilize it.

---

### Post by zero2xiii on 2012-04-17
> **DutchShrek said:**
> I keep running out of time and with the summer being this close I imagine I will have even less time to properly set everything up the way I want it.
So since my Windows PC can stream to xbox and the other can keep my files I can be happy for now.
But I have to leave it at that.

So zero2xiii I wanted to at least post and show my gratitude for your attempt at helping me.
Trust me, if I had the time I would be following your steps to the letter. 

Anyway, thanks a lot for trying to help me. Thanks to the rest of you to share your suggestions. I appreciate the help I got, regardless of not being able to utilize it.

Hay sure no worries :). To bad you don't have the time. Playing around is always fun :guitar:

cherz

---

