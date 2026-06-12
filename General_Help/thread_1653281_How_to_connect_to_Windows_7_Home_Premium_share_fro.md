---
title: "How to connect to Windows 7 Home Premium share from Ubuntu?"
date: 2010-12-26
forum: General Help
---

### Post by ram2500 on 2010-12-26
Hello,

This is an elementary question, but I am having difficulty connecting to a PC that runs Windows 7 (and suffice it to say Windows XP as well). I go to Places > Connect to Server and choose Windows share from the drop-down list. I enter in the computer's IP address in the Server field and click Connect, when I'm brought to the "Password required for x" screen (x being the IP address). I enter my username for the Windows machine, leave the Domain field as is (it is WORKGROUP by default, which is the Workgroup name for both PCs), and then I enter my Windows password. The dialog keeps popping up as if I entered incorrect credentials. I do want to point out, on the dialog, it asks for a Domain name. Since I do not have this computer connected to a domain (I'm at home), it is a workgroup network. However, prior to Ubuntu 10.10, I was able to use this method to connect to Windows computers. Anyone have any insight of the problem?

Thanks and happy holidays,
-ram2500

---

### Post by brdokoky on 2010-12-26
> **ram2500 said:**
> Hello,

This is an elementary question, but I am having difficulty connecting to a PC that runs Windows 7 (and suffice it to say Windows XP as well). I go to Places > Connect to Server and choose Windows share from the drop-down list. I enter in the computer's IP address in the Server field and click Connect, when I'm brought to the "Password required for x" screen (x being the IP address). I enter my username for the Windows machine, leave the Domain field as is (it is WORKGROUP by default, which is the Workgroup name for both PCs), and then I enter my Windows password. The dialog keeps popping up as if I entered incorrect credentials. I do want to point out, on the dialog, it asks for a Domain name. Since I do not have this computer connected to a domain (I'm at home), it is a workgroup network. However, prior to Ubuntu 10.10, I was able to use this method to connect to Windows computers. Anyone have any insight of the problem?

Thanks and happy holidays,
-ram2500

Just use the search on this forum or google or first of all, remove Windows Live ID Sign-in assistant if you have it installed.

[http://ubuntuforums.org/showthread.php?t=1169149]("http://ubuntuforums.org/showthread.php?t=1169149")

---

### Post by Morbius1 on 2010-12-26
Just a further note to what brdokoky already posted. "Windows Live Essentials" also creates the same problem as Windows Live Sign-In Assistant so both will have to go.

---

### Post by Frogs Hair on 2010-12-26
Windows 7 Home Premium can't join a domain it can only be joined to a work group . To join a domain Win 7 Pro is required.

---

### Post by ram2500 on 2010-12-26
I know that Windows 7 Professional and higher is required to join a domain and requires the use of Active Directory, but why is it that I could enter the workgroup name into the Domain field before (in Windows Vista Home Premium) and it would connect, with the fact it was only configured as a workgroup PC?

Just to make sure we're on the same page, what I want to do is connect to a local (within my house) Windows machine, not through Windows Live (to me, Windows Live is a desperate attempt for Microsoft to dress up Windows so it will sell better:p). I use the "Connect to Server" tool in Ubuntu, and from there, choose "Connect to Windows share". This has nothing to do with Windows Live and/or the Internet, just the local network.

Also, when I click on the "Network" folder, I see my Windows computers, but cannot connect using the "Connect to Windows Share" method. Is there an alternate way to go about this? 

I am using my Windows credentials (username, workgroup name, password) and not my Ubuntu credentials.

---

### Post by garvinrick4 on 2010-12-26
Why do you not use Places to Network? You have to set up what you want to be shared
in the Windows machines and set up the Workgroup and have to have a login and password (will not work with auto login.) 
All of my Ubuntu partitions work straight out
of the box in Places to Network. Have to set up printer in the workgroup on each install.
Is really more of a Windows set-up than a Linux set-up. Only takes a few minutes to share
your C: drive and Media and any devices in Windows.

---

### Post by ram2500 on 2010-12-26
File sharing is enabled on the Windows computers, and I haven't "tweaked" anything file-sharing wise on either Windows or Ubuntu. I have tried the Places > Network method, but I still cannot connect. I have included a picture of my computer trying to connect (Ubuntu) with the dialog, which pops up after entering in the credentials as if they were incorrect. 

Keep in mind I'm using my _Windows_ credentials, not my Ubuntu credentials, and none of the computers do not log in automatically.

---

### Post by garvinrick4 on 2010-12-26
#Is your windows machine ram-2500 that it is saying requires password? Need to 
make sure you have set up your workgroup and use same password as required for log-in 
and set windows machine to use log-in at startup. What happens when you try to set up printer? 
Does it show workgroup there? If not it is not setup properly.
#Make sure samba is installed.
```
sudo apt-get install samba
```

---

### Post by ram2500 on 2010-12-27
Samba was installed a while ago; however, do I need to configure anything after installing before I could access a non-domain Windows share? I remember this working "out of the box" with Ubuntu 10.04 and below, and with Vista, which has been upgraded to Windows 7. All of the computers do not auto-login: they all require passwords to login. The printer is not networked as there is no need for it to be, however, it could be if I wanted it to.

---

### Post by Morbius1 on 2010-12-27
The problem isn't that you're using Windows Live Sign-In / Windows Essentials or not. The mere presence of the utility on Win7 is the problem:

[http://lists.samba.org/archive/samba-technical/2010-July/072321.html](http://lists.samba.org/archive/samba-technical/2010-July/072321.html)
> Upon investigation, it was revealed that installing the "Microsoft
Live Sign-On Assistant" modified the spnego transaction to include a
mechToken, which seemingly all versions of samba 3.x.x fail to parse
and always return permission denied.

---

### Post by brdokoky on 2010-12-27
> **ram2500 said:**
> Samba was installed a while ago; however, do I need to configure anything after installing before I could access a non-domain Windows share? I remember this working "out of the box" with Ubuntu 10.04 and below, and with Vista, which has been upgraded to Windows 7. All of the computers do not auto-login: they all require passwords to login. The printer is not networked as there is no need for it to be, however, it could be if I wanted it to.

I told you just remove Windows Live ID Sign-in assistant if you have it installed. I had had same problems like you, that's my solution which works 100% .

---

### Post by ram2500 on 2010-12-27
I never installed anything with Windows Live--I have no need for it. It's one of those softwares that Microsoft produces that has no real use, or can be supplanted by a better product (Internet Explorer, Windows Media Player, etc are not as good or useful as other options...)--

Anyways, since I do not have the Windows Live Sign-in Assistant on _both_Windows XP (my work laptop) and Windows 7 (my personal laptop; dual booted with Ubuntu), is there anything else that may prevent me from connecting successfully. Just as a refresher: **I can see both laptops, and can go only as so far as entering in the credentials for that machine. *However, the password dialog reappears as if I have entered incorrect credentials.***

---

### Post by ram2500 on 2010-12-28
I have read other forums about Ubuntu asking for a password repeatedly when connecting to a Windows share. They, as a commenter has suggested on this topic, were caused by a Windows Live issue. I only have Office 2007 Home and Student, Firefox and Avast installed on the Windows 7 computer; I have not found Windows Live. Is there a way to uninstall it if I do have it? And, *does* Windows 7 come with Windows Live, because I thought that it had to be downloaded. I definitely know that my work PC, a Windows XP Pro computer, does not have Windows Live, yet when connecting to it, it has the same issue. What's going on here???

---

### Post by brdokoky on 2010-12-29
> **ram2500 said:**
> I have read other forums about Ubuntu asking for a password repeatedly when connecting to a Windows share. They, as a commenter has suggested on this topic, were caused by a Windows Live issue. I only have Office 2007 Home and Student, Firefox and Avast installed on the Windows 7 computer; I have not found Windows Live. Is there a way to uninstall it if I do have it? And, *does* Windows 7 come with Windows Live, because I thought that it had to be downloaded. I definitely know that my work PC, a Windows XP Pro computer, does not have Windows Live, yet when connecting to it, it has the same issue. What's going on here???

What's your smb.conf ? Located /etc/samba

---

### Post by Christian Engström on 2010-12-29
> **ram2500 said:**
> I never installed anything with Windows Live
Neither had I on the HP desktop machine that I bought today, but it was factory installed by default.

I had exactly the problem Ram2500 describes, but following Brdokoky's advice to uninstall the Windows Live program seems to have solved it.

Thanks!

To uninstall Windows Live, click 
  Start Menu -> Control Panel -> Programs -> Uninstall a program
and select it from the list.

---

### Post by ram2500 on 2011-01-05
Just in case if anyone refers to this post later on, Windows Live was installed on the Vista machine -and- the XP machine (my work computer). How, I don't know, because I haven't installed either. I feel ignorant. :p
I guess, after a thorough check in the Add/Remove Programs, it was there, lo and behold. I must have skipped over it. 

Windows Live is among the ranks of Internet Explorer, Windows Media Player and Windows ME.

---

### Post by brdokoky on 2011-01-06
> **ram2500 said:**
> Just in case if anyone refers to this post later on, Windows Live was installed on the Vista machine -and- the XP machine (my work computer). How, I don't know, because I haven't installed either. I feel ignorant. :p
I guess, after a thorough check in the Add/Remove Programs, it was there, lo and behold. I must have skipped over it. 

Windows Live is among the ranks of Internet Explorer, Windows Media Player and Windows ME.

I can't believe, you found it ?  Is it working ? :lolflag:

---

### Post by kaikai5816787 on 2011-01-13
> **brdokoky said:**
> I can't believe, you found it ?  Is it working ? :lolflag:

brdokoky you are awesome! This problem had baffled me since windows 7 was released.

I am here to confirm that I just removed Windows Live Essential. All of a sudden, everything worked like a charm.

The only thing left that puzzles me now is that, how on earth was this solution known in the first place?:confused:

---

### Post by tidan on 2012-01-05
Does removing windows live garbage remove the movie maker and picture viewer too?

---

