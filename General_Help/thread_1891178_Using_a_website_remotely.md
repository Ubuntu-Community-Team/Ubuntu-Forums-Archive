---
title: "Using a website remotely"
date: 2011-12-05
forum: General Help
---

### Post by Kissell on 2011-12-05
> 
SITE A  ----- INTERNET ----  SITE B


I am at SITE A.  My files are stored at SITE B.  I want to upload my files to a cloud service like dropbox.  Dropbox has a web interface where I can upload the files, but I don't have access to the files from SITE A.  So what I would like is to use the dropbox website as if I'm at SITE B, while I'm at SITE A.

Any easy way to accomplish this with Ubuntu?  I was thinking there might be an easy and secure proxy or vpn service in the repositories, but I haven't found a good solution yet.  Anyone else doing something like this?

I was thinking I could setup a VPN to site B then remote desktop to a computer in site B and use it's web interface...  but that's a lot more trouble than I want to go through...  it isn't really "me" who needs to use this...  I was hoping I could setup some sort of proxy service easily..  where he could act as if he was coming from one of the servers in site b and it would also show locally stored files on that server at site b when he tried to upload to websites.

---

### Post by 3rdalbum on 2011-12-05
This is so simple to do on Linux and Unix, it's nearly trivial.

You need to install openssh-server at Site B. Pretty sure it will start as soon as it's installed.

At site A, open a terminal and (substituting '<ip-address>' for the actual IP address of the Site B computer) type:

```
ssh -XC <ip-address>
```

You'll be asked for a username and password; this is the Site B computer's username and password, not Site A's! Once you've typed those you'll be sitting at a command prompt on the Site B computer.

You can run graphical programs (because we passed the -X parameter to ssh) by typing them:

```
firefox
```

should be what you want, or you can run the Dropbox indicator applet. The result will be running on Site B's computer, but visible on your Site A desktop. You can interact with this as though you were sitting at Site B.

Once you've done everything you want, you can close the terminal window or type 'exit' at the Site B terminal prompt to close the connection.

If Site B's computer is behind a firewall, you'll need to forward Port 22 on Site B's firewall.

Note that you DON'T need a VPN, because SSH will encrypt the traffic.

Make sure Site B's passwords are super-strong, because there WILL be password cracking attempts. What's better is to use key-based encryption, but you'll have to find a HOWTO about it; I've never had to use it.

Good luck!

---

### Post by Kissell on 2011-12-05
I use ssh all the time, but only in text mode...  kinda forgot it could do X11 forwarding, never used it.

Unfortunately it's telling me: "*** System restart required ***" so I'll have to try later.

I thought doing this would just let me use firefox from SITE B, a way to get around web content filtering, ect...  but inside of firefox, when I browse the hard disk, it will show the SITE B server?  I didn't expect that.  I guess it makes sense...  this will be pretty easy...  

passwords would need to be pretty strict.

it would also be good to somehow limit the internet user to only the "firefox" app...  not allow them to run anything else like "rm"...  although user file permissions should keep it fairly safe.

---

### Post by CrusaderAD on 2011-12-05
Why don't you just setup FTP on both servers? Are you looking for a complete web based solution?

---

### Post by Kissell on 2011-12-05
@3rdalbum: awesome, I was able to reboot the server today and try to connect with ssh X11 and it gave me a normal command line prompt, but when I launched a GUI application like firefox it opened on my local system and when I went to upload files from the browser it was showing me the files on the remote server.  So cool.  I had no idea how easy that would be.

---

### Post by Kissell on 2011-12-05
@CerealCypher: Ftp won't work well for this.  What I'm actually trying to do is give remote non-technically inclined clients an easy way to offload their files from the server in site-b to a cloud service.  

It's a unique situation, I have the user data of tons of users which are independent of each other, but we're getting out of that business, so I need a way for them to get their files to the cloud.  If they FTP them to themselves then they'll have to reupload them to the cloud provider of their choice.  Everyone has a web interface for their cloud storage, so I was thinking the clients could directly send their flies to the cloud service of their choice without giving me their passwords to that cloud service.  

This would save them a lot of time and bandwidth, and would actually help me, because if they FTP from site-b, they are likely to just grab all their data (bandwidth issues for me)...  but if they use a web interface to upload to cloud storage (which charges per gigabyte) then I'm hoping they will be more discerning on what they decide to take and what can be left behind in the trash.

---

### Post by Kissell on 2011-12-05
Thanks guys, this at least gives me a solution that will work, and I can hold people's hands through while they connect the first time.

But, is there a GUI ssh client I can script for the user, or a web based ssh server I can install at site-B?  

I'm guessing (knowing?) most of these users aren't going to have an ssh client preloaded, and a command line is going to scare them.  It would be great if I could just direct them to my website and clicking a button would pull up a local window for them of the firefox browser on the site-b server.  

Also, is there a limit to the number of simultaneous ssh sessions coming in on port 22?  I might need to raise that limit.

---

### Post by Kissell on 2011-12-05
looks like editing /etc/ssh/sshd_config will let me control how many connections and increase security in serveral ways, like not allowing root access.

And I found the following free web-based ssh servers (hopefully one of them will make it easier on the users): 
Ajaxterm
Anyterm
WebShell
Shell in a Box

NOTE: This would effectively bypass the web content filter for users connecting to it...  very cool...  I'll have to set one of these boxes up at home so my friends and family can get on facebook from their offices without being blocked or monitored.

---

### Post by Seq on 2011-12-05
Note that if you're doing X11 forwarding, the client will need an X11 server to display. This eliminates windows (unless you have them install and configure XMing, which you probably want to avoid), as well as some versions of OSX (It used to be an optional component, not sure about the current status).

I can't say I know too  much about the data you've got, or your users. But if it were me, I'd avoid the whole thing, set up FTP and be done with it.

Even if they could do X11 forwarding easily, AND log in to their dropbox via a X11-forwarded firefox, AND start uploading files, there could still be issues. The ssh session could time out, killing firefox mid-upload, etc. What response can you have a year from now when a user calls to say "you" lost some of their data?

---

### Post by Kissell on 2011-12-05
Ouch...  so this isn't even possible from a windows client...

One of the other considerations for wanting to do it this way, is that my site's upload speed is hundreds of times faster than the download speed that the client sites have.  Therefore it would only take a few days to upload their data to the cloud directly from me, but it would take a month for them to download the data from me to them via FTP or any other transfer method...  

I was hoping to give them control to use my bandwidth to move their data to the cloud directly from me.

---

### Post by Seq on 2011-12-06
> **Kissell said:**
> Ouch...  so this isn't even possible from a windows client...

One of the other considerations for wanting to do it this way, is that my site's upload speed is hundreds of times faster than the download speed that the client sites have.  Therefore it would only take a few days to upload their data to the cloud directly from me, but it would take a month for them to download the data from me to them via FTP or any other transfer method...  

I was hoping to give them control to use my bandwidth to move their data to the cloud directly from me.

You could set up some sort of remote desktop. VNC would probably be easiest, as there are web-based VNC viewers. Depends how many customers you have though, as management could be a pain.

You could have them set up some sort of dropbox escrow account, and provide the password (assuming dropbox will allow transferring data between accounts)

Same as above, but have them give you the password for their dropbox account, and have them change it after (hey, you've *already* got their data, right?)

You can install dropbox in a headless config, which requires them to go to a URL to authenticate the machine. [Howto here]("http://dropboxwiki.com/Text_Based_Linux_Install"). You can probably write a script to allow them to ssh in, give them the URL, and then allow the dropbox sync daemon to run in the background, pushing up their data. Not sure if there is some way to check if you are completely sync'd, or if you just need to watch the network...

---

