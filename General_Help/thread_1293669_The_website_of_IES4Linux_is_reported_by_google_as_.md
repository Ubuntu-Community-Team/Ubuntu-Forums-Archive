---
title: "The website of IES4Linux is reported by google as a harmful site"
date: 2009-10-17
forum: General Help
---

### Post by Moses1200 on 2009-10-17
Hello, 
I'm trying to install IES4Linux. I have already installed wine and the other things as i was directed to by this website: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux).
But as i search for IES4Linux in google, it is reported by google as a harmful site. 
website address: [www.tatanka.com.br/]("http://www.tatanka.com.br/")**ies4linux**/page/Installation
google says: [This site may harm your computer.]("http://www.google.com/support/bin/answer.py?answer=45449&topic=360&hl=en&ei=u9jzsutvgsaf_aaan5nhda&sa=x&oi=malwarewarninglink&resnum=1&ct=help/?sa=X&ei=U9jZSuTvGsaF_Aaan5nHDA&ved=0CAgQ2gEwAA")
Is there a safe way of obtaining IES4Linux? 
Thank you

---

### Post by StuartN on 2009-10-17
> **Moses1200 said:**
> Is there a safe way of obtaining IES4Linux?

I would definitely agree with Google that there is no safe way to deliberately install malware on your computer. No security can protect against a user opening back doors, permitting untested executables to run, etc, etc.

The most worrying aspect to Microsoft Internet Explorer for Linux is that Microsoft is unable to provide a certified download site for it, so you are at the maw of any trickster who wishes to provide uncertified copies with unknown payloads.

At least running the native Windows version in Wine or a VM would insulate your Linux system from harm.

---

### Post by MountainX on 2009-10-17
> **Moses1200 said:**
> Hello, 
I'm trying to install IES4Linux. I have already installed wine and the other things as i was directed to by this website: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux).
But as i search for IES4Linux in google, it is reported by google as a harmful site. 
website address: [www.tatanka.com.br/]("http://www.tatanka.com.br/")**ies4linux**/page/Installation
google says: [This site may harm your computer.]("http://www.google.com/support/bin/answer.py?answer=45449&topic=360&hl=en&ei=u9jzsutvgsaf_aaan5nhda&sa=x&oi=malwarewarninglink&resnum=1&ct=help/?sa=X&ei=U9jZSuTvGsaF_Aaan5nHDA&ved=0CAgQ2gEwAA")
Is there a safe way of obtaining IES4Linux? 
Thank you

I used IEs4Linux and it does not cause any inadvertent harm to your computer. I think google is mistaken in this case. The problem is not ies4linux. But Microsoft software itself might be a problem. So you would probably be better off sticking to native Linux software if you can. But, if like me, you need some Windows software, Wine and ies4linux can be great.

Here is my post about how I set up wine with ies4linux:
[http://ubuntuforums.org/showpost.php?p=7963718&postcount=13](http://ubuntuforums.org/showpost.php?p=7963718&postcount=13)

There is also another option. It is possible to install IE in Wine using winetricks. I did not do this because SSL (https) doesn't work. SSL does work if you use ies4linux. But the winetricks method avoids some of the issues (hacks) used by ies4linux so it is more of a pure Wine solution.

---

### Post by Moses1200 on 2009-10-17
First of all, thank you for answering. So you recommend me to install IE to wine?
I need to go into the website of the university and i could find absolutely no way of doing it with firefox.

---

### Post by SPr on 2009-10-17
My (probably mistaken) reading of it is that the site was hacked or perhaps had adverts leading to drive-by downloads of malware. But you are using Linux - Windows crap won't hurt it.

Rather than installing IE4Linux (which I've used in the past with no problems) can you change the useragent in FF to IE? 
Type "about:config" into the address in FF and filter the list for strings containing "useragent". Alter them to reflect a Windows machine.
[List of IE useragent strings](http://www.useragentstring.com/pages/Internet%20Explorer/)

---

### Post by MountainX on 2009-10-17
> **Moses1200 said:**
> First of all, thank you for answering. So you recommend me to install IE to wine?
I need to go into the website of the university and i could find absolutely no way of doing it with firefox.

Your university does not support Firefox?!? That is strange. I think I would complain to the university!

If you must use IE, then yes, Wine will work. Try using Winetricks first. Try this code. I think it will work:

```
sudo apt-get install wine
sudo apt-get install cabextract
wget http://www.kegel.com/wine/winetricks
sh winetricks ie6
```

If that doesn't work, you'll have to read the Winetrick help.

Once you have IE installed via Winetricks, see if you can log in to your university. If they require SSL or something else, you may have to go with ies4linux. If so, you can just remove Wine (using Synaptics) and delete ~/.wine, then start again and use ies4linux instead of winetricks.

---

### Post by MountainX on 2009-10-17
> **SPr said:**
> My (probably mistaken) reading of it is that the site was hacked or perhaps had adverts leading to drive-by downloads of malware. But you are using Linux - Windows crap won't hurt it.

Rather than installing IE4Linux (which I've used in the past with no problems) can you change the useragent in FF to IE? 
Type "about:config" into the address in FF and filter the list for strings containing "useragent". Alter them to reflect a Windows machine.
[List of IE useragent strings]("http://www.useragentstring.com/pages/Internet%20Explorer/")

changing the useragent is a good idea to try first. there is also an add-on for firefox that lets you change useragents easily.

---

### Post by Moses1200 on 2009-10-17
> **SPr said:**
> My (probably mistaken) reading of it is that the site was hacked or perhaps had adverts leading to drive-by downloads of malware. But you are using Linux - Windows crap won't hurt it.

Rather than installing IE4Linux (which I've used in the past with no problems) can you change the useragent in FF to IE? 
Type "about:config" into the address in FF and filter the list for strings containing "useragent". Alter them to reflect a Windows machine.
[List of IE useragent strings]("http://www.useragentstring.com/pages/Internet%20Explorer/")

I did not understand. It's my first day with ubuntu, so i'll be very grateful if you'll have the patience to take it slow with me. I typed about:config but i see so many things there. what exactly do i need to do?

---

### Post by SPr on 2009-10-17
Somewhere in the FF window should be a textbox called "filter". Type "useragent" into it to find all the strings with "useragent" in the name. Or follow MountainXs advice and install the plugin.

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59) Don't know if it works.

---

### Post by StuartN on 2009-10-17
> **Moses1200 said:**
> I did not understand. It's my first day with ubuntu, so i'll be very grateful if you'll have the patience to take it slow with me. I typed about:config but i see so many things there. what exactly do i need to do?

You can add the User Agent Switcher to Firefox (Tools->Addons->Get Addons) which will add a menu to select which browser Firefox reports itself as when visiting websites.

---

### Post by Moses1200 on 2009-10-17
ok, i added the add-on, but it wasn't enough. i think it's because it's a video website designed only for ie with wmp. so i guess i must install those. what do you recommend - wine or vm?

---

### Post by StuartN on 2009-10-17
> **Moses1200 said:**
> I need to go into the website of the university and i could find absolutely no way of doing it with firefox.

> **Moses1200 said:**
> ok, i added the add-on, but it wasn't enough. i think it's because it's a video website designed only for ie with wmp. so i guess i must install those. what do you recommend - wine or vm?

What kind of a university would create its website in a restricted format and require proprietary software of a specific brand to access it?

You should raise this with your course coordinator because it is not acceptable.

---

### Post by Moses1200 on 2009-10-17
I would talk to them. Here is the message i get from the website when i enter it: "The presentation requires Internet Explorer 5.0 or later, Netscape Navigator 7.0 or later, or Internet Explorer 5.2.2 or later for Mac. To download the latest version of Internet Explorer from the Microsoft Web site, click OK."
is it still possible (and recommended) to get netscape and to get it to work on ubuntu? how can it be that something that should work with netscape doesn't work with firefox?
It is written there that it was created with Microsoft Pruducer for PowerPoint 2003.

---

### Post by mechro on 2009-10-17
Does this work?...

[https://addons.mozilla.org/en-US/firefox/addon/8910](https://addons.mozilla.org/en-US/firefox/addon/8910)

---

### Post by darkstaar on 2009-10-17
> **SPr said:**
> My (probably mistaken) reading of it is that the site was hacked...

Yep. The site was hacked. I've alerted the author.

---

### Post by Moses1200 on 2009-10-18
> **mechro said:**
> Does this work?...

[https://addons.mozilla.org/en-US/firefox/addon/8910](https://addons.mozilla.org/en-US/firefox/addon/8910)
  
nope, but thanks:)

---

### Post by Moses1200 on 2009-10-18
> **darkstaar said:**
> Yep. The site was hacked. I've alerted the author.
and if it was hacked, how come it can't hurt me as an ubuntu user?

---

### Post by StuartN on 2009-10-18
> **Moses1200 said:**
> and if it was hacked, how come it can't hurt me as an ubuntu user?

If you download and run executable files from untrusted sources then you may run malicious code. It has been stated that the site has been hacked, so nobody (including the site owners) can be sure of what the Linux executable element of the package does to your system.

Internet Explorer is a Windows program. A safe(r) way of running it is by downloading a verified Windows installer script from the Microsoft domain and installing it in a Windows virtual machine or in Wine, which protects your Linux filesystem from both the installation process and the application.

Running a Linux script of unknown content, from an unknown web site in order to install a Windows program is choosing to bypass the security of Linux.

---

### Post by darkstaar on 2009-10-18
> **StuartN said:**
> Running a Linux script of unknown content, from an unknown web site in order to install a Windows program is choosing to bypass the security of Linux.

In this case, the hacker linked to a malicious script located at google-query.com. I've been in contact with the author of IES4Linus and it now appears that the site has been cleaned up.

---

### Post by Moses1200 on 2009-10-18
> **StuartN said:**
> If you download and run executable files from untrusted sources then you may run malicious code. It has been stated that the site has been hacked, so nobody (including the site owners) can be sure of what the Linux executable element of the package does to your system.
 
Internet Explorer is a Windows program. A safe(r) way of running it is by downloading a verified Windows installer script from the Microsoft domain and installing it in a Windows virtual machine or in Wine, which protects your Linux filesystem from both the installation process and the application.
 
Running a Linux script of unknown content, from an unknown web site in order to install a Windows program is choosing to bypass the security of Linux.
 
I tried to install IE following the instructions of wine and winetricks, but the IE wasn't nothing like IE - it showed hebrew text left to right instead of right to left (without the encoding making any difference) and i still wasn't able to connect to the university website because i could find no way to enter my credentials. is VM the only possibility left, or can i do something else to make it work in wine?

---

