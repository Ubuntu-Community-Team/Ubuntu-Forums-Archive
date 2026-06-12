---
title: "Won't boot into desktop"
date: 2009-09-26
forum: General Help
---

### Post by greenewbie on 2009-09-26
My desktop won't come up automatically now on either of my hard disks I've taken in and out of my computer. As reported in the thread below:

[http://ubuntuforums.org/showthread.php?t=347778](http://ubuntuforums.org/showthread.php?t=347778)



 	 	 [COLOR=Red]It does boot but then it just goes to a black screen like a Fullscreen terminal wich asks me for my login and password then goes into a terminal like mode.
Basically it doesnt load the user interface it stays in a fullscreen terminal mode.
[/COLOR]

 I have the same problem, the Ubuntu load up bar thing goes through ok but then instead of getting the desktop user interface (ie with all programs and icons on it), I get the black screen.  When I entered my login and password, it said:

**“Starting up......loading, please wait**
 [B]19 + 0 records in
19 + 0 records out[/B]
 [B]kinit: [FONT=Times New Roman, serif][[/FONT][FONT=Times New Roman, serif]a load of technical stuff and a series of numbers[/FONT][FONT=Times New Roman, serif]][/FONT][FONT=Times New Roman, serif]

kinit: no resume image, doing normal boot.....[/FONT][/B]
 

 **[FONT=Times New Roman, serif]Ubuntu 9.04 john-desktop tty1[/FONT]**
 [B][FONT=Times New Roman, serif]john-desktop login:    [/FONT][FONT=Times New Roman, serif][I entered it[/FONT][FONT=Times New Roman, serif] [/FONT][FONT=Times New Roman, serif]]
Password: [/FONT][FONT=Times New Roman, serif]    [/FONT][FONT=Times New Roman, serif][I entered it[/FONT][FONT=Times New Roman, serif] [/FONT][FONT=Times New Roman, serif]][/FONT][/B]
 

 [FONT=Times New Roman, serif][SIZE=4]It then finishes with[/SIZE][SIZE=4][COLOR=Black][EMAIL="john@john-desktop"]john@john-desktop[/EMAIL][/COLOR]:~ $ [/SIZE][B]          “
[/B][/FONT][FONT=Times New Roman, serif]
I then tried as [r4ik ]("http://ubuntuforums.org/member.php?u=48311")[/FONT]suggested in the above thread:
  	 	 [B]Log in with you're username and password and do a,

sudo apt-get install gdm ubuntu-desktop

Please post back if it works.[/B]
 

 
It said:
[B]“Reading package lists.....done
Building dependency tree[/B]
 **Reading state information....done**
 

 **gdm is already the newest version**
 **ubuntu-desktop is already the newest version.**
 

 [B]The following packages were automatically installed and are no longer required:

*python-pexpect dar libdar64-4 pmount.*[/B]
 [B]Use “apt-get autoremove” to remove them.”
[/B]
I tried to see if my desktop would load ok, without doing the last instruction. It didn't, so I repeated the operation above and carried out the last instruction but to no avail. The desktop still didn't load and the last thing on the black screen was once again [FONT=Times New Roman, serif]** [EMAIL="john@john-desktop"]john@john-desktop[/EMAIL]:~ $**[/FONT][FONT=Times New Roman, serif]

I´d also like to mention that I took one hard disk (using Ubuntu 8.10) out of my normal computer, I put it in my old computer.  It booted ALL THE WAY to my desktop, no problem; I successfully upgraded it to Ubuntu 9.04 (I was hoping this would somehow solve the problem, even though on my old machine, it kicked me out several times back to the login, when I used the scroll bar!) [/FONT] 
 

 So the situation now is that I can't get to the desktop on either hard disk (the other one is Ubuntu 8.04).
 

 Can anybody help please? :confused:

---

