---
title: "Please read and correct me if I'm wrong (Linux security)"
date: 2010-07-23
forum: General Help
---

### Post by schwabdale on 2010-07-23
I am new to Linux. I am trying to understand the Linux structure and why its so secure and almost virus free. Please correct anything that may not be right. Thanks in advance!

_Viruses_			
 

 User privileges
 [SIZE=2]By default, the Windows user is given full administrative access to every file on the computer. This includes installing programs, accessing/changing the registry, and the the ability to delete anything they want to delete. When a virus enters the computer, it inherits [/SIZE] 
 [SIZE=2]these same privileges. Within windows, every file has full access to every other file on the system. If a virus enters the system, it has full administrative access to the entire computer, making it easy to spread itself throughout the system. [/SIZE] 
 [SIZE=2]In Linux, the default user is not given this administrative access to the entire system. They are only given full access to their user folders. [/SIZE] 
 If the user wants to perform an administrative task such as deleting a system file, they have to put their password in to run as the administrator of the computer. If a virus was to enter a Linux system, it would first have to crack the password.... but there's still a problem. The virus would then have to write itself to other files on the system. The Linux file structure does not give full access to a file trying to access another file like Windows does, making it very difficult for a virus to move throughout the system.  
 

 File Level Security/Structure  
 [SIZE=2]Windows has a very complex file structure. For example, when you install software, it installs to the program files folder. There are also [/SIZE] 
 [SIZE=2]different values added to the system32 folder. There are then values added to the registry. Windows also uses .dll files. These files link the software to the rest of the system. For all this to happen, each file or folder must have full access to everything else on the system. This makes it easy for a virus to worm its way through the system without any security concerns. [/SIZE] 
 [SIZE=2]With Linux, each file stands on its own. Software gets installed in a single location and only grants minimum access to everything else on the system trying to access it. Its not linked up like Windows. If software crashes, it doesn't crash the entire system... because it stands on its own. [/SIZE] 
 

 Firewalls/Open ports
 [SIZE=2]Windows has many open ports in the operating system. These ports allow software, internet traffic, file sharing, ect... to pass through them. When you are on the web, your Windows computer opens a port for Internet Explorer to pass through to the web. When you download a file from a website, it must go through a port. This is where a firewall comes in. A firewall tries to monitor and block access[/SIZE]
 [SIZE=2]to unwanted traffic. Many viruses infect your computer through these same ports. This is the doorway they pass through while your on [/SIZE] 
 [SIZE=2]the web. Obviously, many viruses get past the built in Windows firewall. [/SIZE] 
 [SIZE=2]By default, Linux does not open all these ports. In fact,, Linux does not even use the same ports to perform the same work. There is a very [/SIZE] 
 [SIZE=2]powerful built in firewall. Its called Iptables. If Linux does not recognized the traffic coming through the port, it just blocks access. That simple. [/SIZE] 
 

 Minimal damage
 [SIZE=2]When a virus hits a Windows system, it can easily damage the entire system rendering it useless. [/SIZE] 
 [SIZE=2]For a moment, lets assume Linux has been infected by a virus, chances are the most it can do is delete your user files. If these files [/SIZE] 
 are important, you should be making backups of them anyway. But, the odds of a virus rending your entire system useless is slim to none.  
 

 Market share
 [SIZE=2]There are many, many Windows computers on the market. Many, many people do not like Microsoft. For whatever reason, Microsoft [/SIZE] 
 [SIZE=2]has a lot of enemies who know its very easy to exploit their system. Most viruses are made for Microsoft. They only infect Microsoft. [/SIZE] 
 [SIZE=2]This is their goal. If a virus writer wants to do as much damage as possible, why would they write a virus for a system to damage a few files when they could potentially damage millions. [/SIZE] 
 [SIZE=2]Linux has a very small market share. They are no where near the target Windows computers are. Even if they where a target, they would [/SIZE] 
 have a very difficult time making a successful Linux virus.  
 

 The amount of viruses
 There are currently thousands of Windows viruses. There are currently less than 100 Linux viruses. Out of these Linux viruses, only a few are of any concern.  
 

 Summary
 [SIZE=2]To date, there are no known Linux viruses running in the wild. This means there are no viruses jumping from computer to computer. The odds alone say your chances of getting a Linux virus are slim to none.[/SIZE]
 [SIZE=2]Linux is built based upon the Unix operating system. Unix is the most stable virus free operating system created. This operating system [/SIZE] 
 [SIZE=2]was built for networks, not users. In a network of computers, you don't want everyone having access to everything on the network. [/SIZE] 
 [SIZE=2]With the same idea in mind, the Linux operating system limits the users ability to access or perform potentially destructive tasks within the system.  [/SIZE] 
 [SIZE=2]Windows is based on the users experience. Windows has made the users computer completely open for the user do whatever they want. Virus authors known this, and exploit it. [/SIZE]

---

### Post by ubunterooster on 2010-07-23
Very true except for > [SIZE=2] Windows has made the user's computer completely open for the user do whatever they want.[/SIZE]but lets not go to far there.

Also consider that UNIX (which actually had the first viruses) and Windows were first built in pre-internet days. Linux differs from UNIX in the build more than most realize

---

### Post by rushikesh988 on 2010-07-23
nice study dude ...

---

### Post by schwabdale on 2010-07-23
[LEFT]Thanks, I just hope I'm fairly accurate. I wasn't sure exactly about how many Viruses there where. 
[/LEFT]

---

### Post by Goolie on 2010-07-23
> **schwabdale said:**
> [LEFT]Thanks, I just hope I'm fairly accurate. I wasn't sure exactly about how many Viruses there where. 
[/LEFT]



Sounds about right to me!

:popcorn:

---

### Post by ubunterooster on 2010-07-23
Howmany? Between 7 and 40

good read on why:  [http://librenix.com/?inode=21](http://librenix.com/?inode=21)

To pop your feeling of invincibility: [http://www.geekzone.co.nz/foobar/6229](http://www.geekzone.co.nz/foobar/6229)

---

