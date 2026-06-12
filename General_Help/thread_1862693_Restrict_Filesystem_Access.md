---
title: "Restrict Filesystem Access"
date: 2011-10-17
forum: General Help
---

### Post by frozen.fire on 2011-10-17
Hi,

I have several users on the ubuntu 10.04LTS (64-bit) machine and most of them will be online simultaneously using RDP(xrdp). The users include members from my AD domain who are on roaming profile(their home folder will be reset automatically on log out).

Now the challenge for me is to restrict all the access(including read... execute is ok) for each one of them to all of the filesystem and applications except their own home directory and ability to use applications like libre office, thunderbird, gnumeric (apart from calc in libre), firefox(with flash plugin), pdf viewer, image viewer and (maybe) few other applications. I dont want them to be able to even access terminal. In short, they will have pretty much the only previlages i mentioned earlier. I also want 2 users that i create locally to have the sudo permission.

Now, im a little confused. How do i achieve this? I know this might sound a lame, but i'm kind of a newbie. I will appreciate a step by step procedure to achieve this, i'm not an expert with the linux system yet (managed a lot of stuff till now and still learning a lot :)).

Please dont ask me to use Google (i already did but not helpful.), i even searched the forum but could not find anything much helpful.

---

### Post by An Sanct on 2011-10-17
Greetings!

The user management is rather simple (and secure/strict) in Linux :). Here are two pages, that cover this:
[Managing Users in Ubuntu]("http://www.freesoftwaremagazine.com/articles/users_in_ubuntu")
and a slightly more technical from ubuntu.com
[User Management]("https://help.ubuntu.com/8.04/serverguide/C/user-management.html")

I hope this covers your question! If you still have questions, feel free to let us know ;)

Cheers!

---

### Post by frozen.fire on 2011-10-17
I will definitely look into the documents. i'll see if these help. thanks a lot.:)

---

### Post by frozen.fire on 2011-10-18
Well thanks for the links An Sanct, I have already gone through the ubuntu help previously, the comprehensive article [Managing Users in Ubuntu]("http://www.freesoftwaremagazine.com/articles/users_in_ubuntu") was good too. These articles could not quite solve my problem.

Let me re-draft my earlier post. I'm trying to setup a network of Ubuntu 10.04LTS machine (remote access on machines with only thinclient boxes and no local hard drives) in an existing windows environment. I need to use the existing AD authentication which makes it clear that the login at the client side will not be specific to user (anyone can login any thinclient). This objective is kind of achieved using Likewise-Open and XRDP.

Another challenge would be to restrict the users from roaming around the system and read/modify files (like we had previously on our windows network, no user could access the folders other than the ones configured for their group).

Third objective is to enable everyone who can login to access a few applications only like mail client (evolution/thunderbird), Gnumeric, Libre office, browser (firefox/chrome), pdf viewer, image viewer etc. Though I understand that no user will be able to do any shabby stuff using the terminal without sudo, I wish to to disable terminal (as well as Administration and preferences menus) for these users.

I read somewhere that the restrictions can be set through the use of winbind and samba but didn't explain how. So, I read a few articles including [ActiveDirectoryHowto]("https://help.ubuntu.com/community/ActiveDirectoryHowto")  [ActiveDirectoryWinbindHowto]("https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto") and [Configuring Samba]("https://help.ubuntu.com/6.06/ubuntu/serverguide/C/configuring-samba.html") 
I couldn't find out a way yet. They explain how to configure these services for authentication but nowhere i found anything about configurations to achieve my objectives above.

Please help !! My boss is after my life and has given the deadline to implement this by 24th october. I'm all on my own and there is nobody here in the office to help me on this. :sad:  Im not yet an expert on *nix OS, so, please give a detailed solution on how to achive this or a link where it explains in a way that a noob like me can understand.

Thanks in Advance.

FF

---

### Post by frozen.fire on 2011-10-18
I finally figured out how to stop users from accessing each other's home directories. The solution was [here]("http://www.pc-freak.net/blog/how-to-configure-debian-to-create-new-added-users-through-adduser-to-be-secure-by-default/")

Moreover, I decided to remove/uninstall most of the useless applications. All the authentication through RDP on AD was successful and people were able to access the fileserver without problem as configured in AD.

One challenge i'm facing right now is that whenever a user is loggong in through RDP from a thinclient, everything is so dead slow. However, when i login on ubuntu with the same username(from AD) on my personal laptop(Win XP) through RDP everything seems to work normally. What could be the problem? how to rectify this?:confused: How to find the root of the problem? I thought that the remote thinclient should also use the resources from the ubuntu machine. If it does, all this does not make any sense because the Rame on ubuntu is 4GB and its the only user logged in. ](*,)

EDIT: I have deliberately left the thread unsolved as there is still a problem mentioned. I will mark it solved once i'm successful with this.

---

### Post by frozen.fire on 2011-10-19
For the love of god, can somebody help me here...For most advanced users here, my problem must be tiny but it is important to me. Help me here already people...I dont want to leave ubuntu and go back to windows it is a useless OS like a box out of which u cant configure. Ubuntu is good, please help me....

---

### Post by An Sanct on 2011-10-21
Okay, I will try my best, to help you here, but note (my advice to you) that it will be best if you create another thread with the specific question you want answered. The problem is, that 95% of ppl do not look at "old" threads and threads, that have answers (more than one post).

Here is a [simple RDP howto]("http://www.liberiangeek.net/2010/07/connect-ubuntu-10-04-lucid-lynx-remote-desktop-windows-machines/").
A nice three page tutorial also on [HowToForge]("http://www.howtoforge.com/configure-remote-access-to-your-ubuntu-desktop")

You have a "server - client" situation here, so the server does all the work and the client just displays an updated picture of what is going on (the basic RDP thing).

As with all RDP stuff, try not to use 3D, as it is a resource eater and will slow down the performance. So, for best performance, switch off all the 3D effects, wobbly windows, close/open animations, 3D Cube, 32bit color depth, ...

You are also talking about a "*thin client*" AFIK a thin client is a web application, please be more specific about this. If it is a web application, which browser, if not, which program is it?

---

### Post by kaspar_silas on 2011-10-21
You said you don't want your users to access terminal, the filesystem or view any funky graphical effects. From the user side that seems to be pretty much no actual ubuntu exposure then. 

All the applications you mentioned have good cloud/browser based alternatives (Firefox/Chromium and Google Docs maybe).

Well maybe I am missing something but couldn't you just use these instead? All the sharing and scalability will be done for you then. Plus if you aren't experienced in admin this solution will be far more secure, resilient and backed-up than you will be able to manage in a short time. 

I am certainly not trying to put you of ubuntu but I'd go the safe path first especially if it's job critical.

---

### Post by frozen.fire on 2011-11-01
Marked the thread solved as my initial question was solved and i don't think there is any point continuing with the same thread for further issues or queries. Anyway, thanks everyone that helped or atleast tried.

Cheers!!..

---

