---
title: "Sending files from Windows computer to Ubuntu computer"
date: 2012-06-22
forum: General Help
---

### Post by leopoldbirkholm on 2012-06-22
Hello dear Linux users,

Since English is my second language, I need some help on how to search. Yes, an answer is always nice, but I wish to learn. With that said, here is what I am trying to do.

**The goal**
Send files from my Windows computer to my Ubuntu computer that serves as an media center.
**The rigs**
The Windows computer is an desktop running Windows 7 Professional 64-bit connected to a switch via Ethernet. The Ubuntu computer is an desktop, model HP DC7100, running Ubuntu 12.04 Precise Pangolin 32-bit connected to the same switch via Ethernet. The Ethernet is a standard 100 Mbit system.
**The question**
Right now I cannot see the Ubuntu from my Windows computer but I can see Windows from Ubuntu. The thing that I cannot solve is what I shall search for. Samba-settings? Configure home network? Checking the IP-adresses? So, please, teach me what to search for and I will find a solution. I do not think I am  the first with this issue so please help me find good keywords to search for.

Thank you.
Leopold, Sweden

---

### Post by LewisTM on 2012-06-22
The best is to setup samba user shares. The process may differ depending on the *buntu you use (Kubuntu in your case?). If you never log on to your media server then it gets a bit more complicated 'cause you need to setup your Samba server by hand by editing text files. [Webmin]("http://www.webmin.com/") can help you do that though a web interface.

A second option is to setup Dropbox or Ubuntu One on both machines. It may well be the most dumb-proof way of sharing files but it give you little control on *where* you put them.

Another option is to install SSH. Then use [WinSCP]("http://www.winscp.net") to login to your Ubuntu IP address with your name and password. That allows you to transfer files by SFTP. This is great for file transfers but not a true 'sharing' method.

---

### Post by Lee_Bo on 2012-06-22
If you are a Google user (and who isn't, these days) you could log into your account from both computers and use Drive.

---

### Post by SlugSlug on 2012-06-22
I'd install ssh on ubutnu and use winscp on windows,

---

### Post by steve7777777 on 2012-06-22
> **LewisTM said:**
> The best is to setup samba user shares. The process may differ depending on the *buntu you use (Kubuntu in your case?)...

Samba is one of the best things about Linux, imo. Create a samba share and on the Windows machine map it to a drive - Drive S or whatever. 

As mentioned, Webmin will be a big help. You can use it to edit, start/stop the Samba server when configuring. You'll need to download Webmin directly from their site.

---

### Post by Morbius1 on 2012-06-22
> Right now I cannot see the Ubuntu from my Windows computer but I can see  Windows from Ubuntu. The thing that I cannot solve is what I shall  search for. Samba-settings? Configure home network? Checking the  IP-adresses? Open Nautilus
As a test right click a folder you own like: Downloads
Select "Sharing Options"
Select all the options
Select OK

It may ask you if you want to install Samba ( I think it calls it "windows Networking" or some other daft thing ) - Select OK.

When you are all done you will have created a samba share.

As a test of that share run the following command which should list every workgroup, and within each workgroup every host, and within each host every share on your lan including the one you just created through Nautilus:
```
smbtree
```If there are errors post the entire output of smbtree along with the output of the following commands:
```
testparm -s
``````
net usershare info --long
``````
hostname
```

---

### Post by leopoldbirkholm on 2012-06-24
> **SlugSlug said:**
> I'd install ssh on ubutnu and use winscp on windows,

Thank you SlugSlug. Would you use the SSH Client or the Server? So I know which one I should study more careful.

---

### Post by sudodus on 2012-06-24
> **leopoldbirkholm said:**
> Thank you SlugSlug. Would you use the SSH Client or the Server? So I know which one I should study more careful.
The ssh server should be installed on the computer that should act as server, and a client program (ssh or winscp) should be run on the client from where you want to log in to transfer files. I suggest to let the Ubuntu system be the server and run winscp in the Windows system.

---

### Post by HiImTye on 2012-06-25
in most cases you can still access the Ubuntu computer even if it is not visible for whatever reason from the Windows computer. just access the Ubuntu computer by name in Windows Exploder.

---

### Post by zombifier25 on 2012-06-25
> **HiImTye said:**
> in most cases you can still access the Ubuntu computer even if it is not visible for whatever reason from the Windows computer. just access the Ubuntu computer by name in Windows Exploder.

Windows doesn't have support for ext4, not without a driver (and it's read only, write support is experimental)

---

### Post by HiImTye on 2012-06-25
> **zombifier25 said:**
> Windows doesn't have support for ext4, not without a driver (and it's read only, write support is experimental)
who said anything about ext4? this thread is about samba..

---

### Post by sudodus on 2012-06-25
> **HiImTye said:**
> who said anything about ext4? this thread is about samba..
samba or ssh. Both will work, and it is up to the OP to choose ;-)

---

### Post by zombifier25 on 2012-06-25
> **HiImTye said:**
> who said anything about ext4? this thread is about samba..

Oops, I thought you are talking about seeing an Ubuntu computer directly inside Windows.
Yep, Samba will do it.

---

### Post by leopoldbirkholm on 2012-07-06
Yeep, Samba is the s**t.

Found this video when looking through her channel on my new table. 

[http://youtu.be/deb2jRm3c7g](http://youtu.be/deb2jRm3c7g)

That explained everything. With some tweeking it now works sweet with transfering files from Windows to Ubuntu and back.

Thank you all for sharing your thoughts on the subject!

I will later post the way I did it.

---

### Post by leopoldbirkholm on 2012-07-17
[IMG]http://de-motivational-posters.com/images/thank-you-for-removing-all-doubt.jpg[/IMG]

---

