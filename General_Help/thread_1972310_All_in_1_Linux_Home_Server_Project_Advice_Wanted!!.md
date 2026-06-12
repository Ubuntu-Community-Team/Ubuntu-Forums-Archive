---
title: "All in 1 Linux Home Server Project: Advice Wanted!!"
date: 2012-05-03
forum: General Help
---

### Post by hardcorepber on 2012-05-03
New to the forum! Any advice or knowledgewould be great.
 
Build Mission:
 
My mission is to accomplish an all in 1 home server option. Imcurrently running freenas on the hardware below, but wish to expand. What kindof level of Linux knowledge to complete this? Ive taken class on Unix/Linux, I knowbasic commands and know the VI editor and the Linux environment. I been leaningtowards Ubuntu Desktop distro because anything I cannot do in CLI, can beconfigured in the GUI(OR so I thought). What are your feelings on this? Is therea better distro for my purpose? Ive looked into Amahi, but I didn&#8217;t find it capableof accomplishing all of my needs.
 
I basically want to be able to access everything on my home network, outsidemy network while I&#8217;m away using a registered domain(Example: [www.myname.com]("http://www.myname.com") . Iwork full time and go to school part time(CIS major). Because of this, I needaccess to all my files and documents from my home via a web browser. Onceeverything is up and running, I want to keep it that way. How do I back up allthe configuration files and installs on the server so I don&#8217;t have to go in andreconfigure everything from scratch? I envision all my media on the two 1TBharddrives. Is there a way to administer all of this from 1 online GUI, usingwebmin or something similar? Do you see any foreseeable problems and can thisactually be done on a dedicated mid range desktop below? I wanted to run thisby everyone, and see what everyone thoughts were.
 
I&#8217;ve been googling for dayslooking for complete guides or step by step walk through with little luck. Anyadvice or assistance is greatly appreciated.
 
Additional Questions I have:
What kind of level of Linux knowledge to complete this?
How would you implement this?
How would I document the install, configurations and TESTing?
Security, how to keep the server secure?
 
Hardware:
 
AMD quad core CPU
6 gb ddr3 ram
Two 1 tb green drives
One 160 gb drive
And plan on adding more drives as needed.
Coolmaster half case
Tv tuner card
 
 
The below are my software needs:
 
1.)I want to be able to upload/download files from my Android smartphonevia SFTP to a server directory, which syncs with iTunes folder Automatic add toiTunes folder on my Macbook.
 
2.)OpenSSH to login and administer
 
3.)Torrent downloader with a web GUI, to download torrent while im away
 
4.)Owncloud linked to Samba Shares for local network access and remoteaccess
 
5.)Music streaming server(Like subsonic)
 
6.)VNC server
 
7.)VPN server
 
8.)Document management system. Using openKM or fengoffice to have centralizeddocuments I can edit on the go accessible via web browser saving it back on theserver.
 
9.)UPNP for PS3 streaming or other devices on my LAN
 
10.)Media tomb back end to record tv shows
 
11. Samba shares
 
12.) SFTP server using vsftpd
 
13.) Backup plan: I want the server to back up folders or directoriesfrom my Macbook Pro and Win7 desktops I then want to back this information fromthe server to a external esata hard drive. [COLOR=red]QUESTIONS:how would I accomplish this?[/COLOR] 
 
14.) virus scanning
 
Optional:
 
Email server
 
 
Thanks for your help and for reading!:)

---

### Post by weryl on 2012-05-03
Hum that's a lot of questions for a single thread, but I think you can accomplish all of that with Ubuntu server. I have a similar server at home and I can't see a reason why you couldn't use it to fill your needs.

I think I've already used something like webmin to administer the server with a web interface but I haven't used it much and I tend to use nano (or vim) to edit my config files manually. But I'm sure that there's a bunch of softwares out there that would do the trick.

1) I think a SAMBA share (for windows file sharing) would cover most of that, and perhaps use another tool to sync your phone through SSH. However I would tend to use something like a normal sync (sambe) when the phone is on LAN so that it happends asynchronously (and so you wouldn't have to overtax your phone connection). The PC and Mac computers should be able to synchonize themselves to the samba share.

2) OpenSSH, installed by default.

3) I use rtorrent, which you may use easily with SCREEN so that it keeps downloading when you're not looking. Personnaly I've set up a seperate user "data" which has "screen -R" in its ~/.profile so that it resumes automatically on login. Also rtorrent monitors a samba share /data/Torrents for new torrents downloaded from any other computer, and starts them automatically.

4) As you said, I'd look into Owncloud (can't get dropbox working on my server).

5) I'd use MPD, or minidlna if applicable.

Don't really know for the rest. Hope it helps!

---

### Post by sharshofski on 2012-05-16
IMHO the best way to dive into most of these things is Google &&|| the forum search bar. I'd say you should just go for it. There are great guides for a lot of the stuff you've mentioned. Basically if you put in the necessary reading time, you'll be able to do most of this stuff in a couple weeks.

1) Easy. There are [a billion]("https://www.google.com/search?client=ubuntu&channel=fs&q=android+sftp&ie=utf-8&oe=utf-8") Andriod sftp clients.

2) Same as before, but don't forget to use [public key crypto]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") instead of passwords!!!!!!

3) Easy for commandline, idk for GUI. I use [rtorrent]("http://libtorrent.rakshasa.no/") running on a [screen]("http://www.slac.stanford.edu/grp/cd/soft/epics/extensions/iocConsole/screen.1.html") instance, so I can access it via ssh. rTorrent needs some work to get magnet links to work properly though... I've used Transmission (GUI) through ssh w/ x-forwarding, but that means you need to maintain the ssh connection while the torrent runs. Try rtorrent.

4) IDK. I've never heard of OwnCloud until now... depends on how good their doc is.

5) Easy. Subsonic is [a breeze to set up]("http://www.subsonic.org/pages/installation.jsp#debian").

6) [vino]("https://help.ubuntu.com/community/VNC/Servers") is great!!

<I don't have the right representations/pointers for 7-11>

12) Easy, same as 2

13) Shouldn't be too hard... there are [so many]("https://help.ubuntu.com/community/BackupYourSystem") backup managers. At worst, you'd need to put some rsync scripts on crontabs.

14) [here]("https://help.ubuntu.com/community/Antivirus")

15) [here]("https://help.ubuntu.com/community/MailServer")

---

### Post by HermanAB on 2012-05-16
Howdy,

The only problem with a 'do everything' server is maintenance.  When you need to fix something on one service, you risk rebooting the whole house of cards.

The solution is virtualization.  If you run Virtualbox, then you can run a vertual server for each major service and keep them independent.  If you have four virtual servers, then you can work on one and crash and reboot it without affecting the other three.  It also takes care of incompatible software libraries which can be a real bummer if you try to run two services that need different, incompatible libraries.

---

