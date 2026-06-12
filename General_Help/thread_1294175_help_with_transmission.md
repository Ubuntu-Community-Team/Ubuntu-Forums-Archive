---
title: "help with transmission"
date: 2009-10-18
forum: General Help
---

### Post by aneneme on 2009-10-18
I am new to ubuntu and have come across a few issues i am hoping someone can help me with.  

First I have ubuntu netbook remix installed on an asus 900 series netbook with a 4 gig SSD.  

My issue is with downloading torrents using transmission.  When I first try to download, I direct it to my TB external hard drive, however it always wants to download onto my SSD.  Then if I try to remove the download from transmission and retry directing it, the window with the option to either 'open' or 'save' does not show transmission as my default for opening anymore.  When i browse for transmission i can't find it in user/bin.  

Obviously i have very little idea what i am doing.  Ive tried to search the forums on similar issues but for me looking in forums is like trying to find a perfect girl.  (no offense to anyone.)  

I have gone into transmission's preferences and selected my external HD as my default but it does not save my changes and doesn't work.  

Also just to help narrow down:
When i first installed Ubuntu i had the common issue where after i switched to classic desktop mode and logged off/restarted my computer everything disappeared.  
What i did to fix this was the following:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
download desktop_switcher_0.4.6_i386.deb 

 in terminal
remove current desktop switcher:
"sudo dpkg -r --force-all desktop-switcher"

check:
"rm -rf ~/.config/desktop-switcher"
this should fail saying directory does not exist [however this did not fail for me]

install newest desktop switcher:
"sudo dpkg -i desktop-switcher_0.4.6_i386.deb"

restart computer or log out/log in
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
This worked for me on my Asus and not for either of the other two laptops i tried it with.

Any suggestions or help will be much appreciated.  Thanks

---

### Post by Charles Kerr on 2009-10-22
> **aneneme said:**
> My issue is with downloading torrents using transmission.  When I first try to download, I direct it to my TB external hard drive, however it always wants to download onto my SSD.

You can set the default download directory in Edit > Preferences

[quote=aneneme]Then if I try to remove the download from transmission and retry directing it, the window with the option to either 'open' or 'save' does not show transmission as my default for opening anymore.  When i browse for transmission i can't find it in user/bin.[/quote]

I'm not sure I understand what you're saying here.  However if you're trying to move torrents from your SSD to your external drive, you should use Transmission's "Set Torrent Location" option, which is available in the File menu in the version of Transmission that ships with Karmic.

---

