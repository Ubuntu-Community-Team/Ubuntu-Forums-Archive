---
title: "Cannot see 'tick boxes' and other contents when installed programmes using Wine"
date: 2010-10-14
forum: General Help
---

### Post by noob2noob on 2010-10-14
Hi!

I have installed ubuntu out of an error, a bit of frustration, a bit of   annoyance and a bit of excitement! I am (was!) a windows user. I had   windows 7 on my laptop. You might already know how famous windows is   with nasty viruses. I got one too! Had no option but to get rid of the   whole OS. I installed ubuntu - mainly because it was free! But the main   factor was, google said, it's not that hard to learn using ubuntu! So I   had to give it a go after being annoyed at Windows - it ruined my   documents! Rant over.

So now, I have ubuntu. Love it to bits. Like the new things I am finding. Few things I am very used to in Windows are:
[LIST]
[*]Microsoft Office
[*]Driving test (UK) on CD
[*]VPN Client at my Uni
[*]Minitab and SPSS softwares at Uni
[*]My Seagate hard-drive which is password encrypted
[*]and few more..
[/LIST]


 but the once listed above are major and daily used programmes (when I   had windows!) My university does not support anything to do with Linux   so this forum is THE hope for me!


 I found WINEHQ over the internet. Installed it. I don't know if I  have  correct packages etc with it. But it mostly runs all my .exe  formats  when I tried to install them. It installed Minitab perfectly and  so it  did with Spotify. What it din't install well is my Driving test  (UK) CD  and Microsoft Office - It installed them but the 'tick boxes'  and some  other contents are not visible at all. It opens a grayish  windows like  box with nothing written in it! It runs the CD but with a  huge gray  screen and nothing to read or click on it!!


 It din't install SPSS and gave me string of errors! And same was the case with VPN!


 As for my hard-drive - it doesn't like it! It doesn't mount it! (I   guess because it's got a Seagate manager.exe that needs to be   installed). So I tried Wine to see if it installs. It installed the   setup but then does nothing! Can't mount it! I am guessing it's because   of encryption, but is there no way around it?


 I don't have Windows anymore on my laptop. I don't intend to ever go   back to windows! But these are some key programmes I need daily with my   project, studies and work! If I can get them working, I can save myself   from living terrible computing life with Windows! [IMG]http://linux.unix.com/images/smilies/frown.gif[/IMG]


 Please help me!!


 Ps: As my name says, I am a complete noob with Linux language,   terminal commands, etc. If there is a solution, please can you give me a   step by step noob language guide? I hope there is someone out there  who  will save me from going back to Windows.. I love Ubuntu, please  save me  from Windows!!

---

### Post by noob2noob on 2010-10-15
Bump!

---

### Post by SavageWolf on 2010-10-15
Why do you need MS Office? Can't you just use OpenOffice?

---

### Post by noob2noob on 2010-10-15
I am using Open office for now. But I have noticed when I try to open documents created in MS Office, they tend to loose the formatting. I have papers and thesis that are about 500-600 pages worth of graphs, tables etc and it is nearly a nightmare to edit all of them again :(

But if that's not possible, I don't mind doing it for couple of days and then create new documents in OO.

The only vital thing is installation of CDs/DVDs/External hard-drive. Can't seem to find answer to it anywhere! :( But I have most of my back up on these medias :shock:

---

### Post by brookie on 2010-10-15
Hey there, and welcome to Ubuntu forums. 

1. Open office is pretty good. You can save your documents in .doc format for MS users, or in regular format if you're the only one using the. I still think MS Excel is better for data analysis and haven't tried the Ooo spreadsheet for this task.  

Once you learn some more, you may be able to install Virtualbox by Oracle. Not ose. The ose version does not support usb devices which sucks.

I run WinXp as a guest host in Virtualbox-3.2 on my Ubuntu lappy. Then I installed Office 2003 and other MS programs I need there. I don't surf the net in Windows because I didn't want to install all the crappy antivirus, antitrojan, antibs sw anymore. 

Most of the time however, I really don't need Office. Only once in a strange while.

2. The external drive. Is it a usb drive? If so, plug it into a Windows machine, and use the remove hardware tool in the Windows task manager before you unplug it. This may be the problem. Happened to me once. On my Seagate external drives I had to plug them into WinXP and use the seagate sw to turn off the power saving feature. Some people have posted that once the drive stops spinning, that Ubuntu could not detect it any longer. I did this on two external usb seagate hdds and they are running fine. 

3. As for the school VPN, I had the same problem at my University. Do they use Cisco VPN? If so, open up the Synaptic Package Manager and search for Cisco. Install vpnc and network-manager-vpnc. You will need the settings from a sys admin at school. I just loaded Cisco vpn for WinXp and opened up the edit settings there to copy them to my Ubuntu setup. This is a little tricky because the Network Manager plugin doesn't have the exact same settings as the Windows forms. 

Good luck and with a little searching on google you'll be able to figure it all out. Put your OS version in your profile too. That way folks here at the forums will know what version of Ubuntu you are on. 

Cheers, 
brook

---

### Post by noob2noob on 2010-10-15
Thanks a lot mate!!

That sounds re-assuring to me. I have tried the idea with hard disk and it din't work. I am still trying it all the time to see if it will just click some time! I have External 320 GB hard drive with USB inlet. It's password protected. My ubuntu does recognise it and even mounts it, but then it doesn't show me the dialogue where I can enter password to be able to view my files!

I did Cisco VPN after upgrading to 10.10, but I think I am messing up the config settings, so I will contact my sys admin at school and see how it goes. 

For virtual machine, do we have to install windows again? I don't have windows at all! I have used all my partition space for ubuntu. Does this mean, I will end up paying those windows people for using them virtually? :O Feel like I should pay ubuntu for using it totally! It's worth it. If it's not buying new Windows CD, can you please help me on how to do it? I have downloaded virtualbox.

---

