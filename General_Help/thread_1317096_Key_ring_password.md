---
title: "Key ring password"
date: 2009-11-06
forum: General Help
---

### Post by dox_drum on 2009-11-06
Hi people!

Since I install Karmic in my laptop, at any startup asks my for a key-ring password (or something like that) to connect to internet.

Is there any way to stop this? i. e., automatic connection or whatever.

Thank you!

---

### Post by Giblet5 on 2009-11-06
> **dox_drum said:**
> Hi people!

Since I install Karmic in my laptop, at any startup asks my for a key-ring password (or something like that) to connect to internet.

Is there any way to stop this? i. e., automatic connection or whatever.

Thank you!

Install "wicd" from synaptic and remove the network manager applet from System -> Preferences -> Startup Applications.

That will remove network-manager and install a different mechanism with a better interface, a better icon, and no annoying authentications.

---

### Post by jbrown96 on 2009-11-06
[http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/]("http://johnny.chadda.se/2007/02/21/unlock-the-gnome-keyring-upon-login/") This looks like a good guide that should be simple to follow. If that doesn't work, then you can go into the keyring (in system-->preferences or system-->admin) and delete it. Logout. When you login, you will probably need to re-add your network password. When that asks for a password for the keyring, just leave it blank, and ok the warning message.

---

### Post by jbrown96 on 2009-11-06
> **Giblet5 said:**
> Install "wicd" from synaptic and remove the network manager applet from System -> Preferences -> Startup Applications.

That will remove network-manager and install a different mechanism with a better interface, a better icon, and no annoying authentications.

Don't do this. Wicd is unnecessary. This doesn't solve the problem, it just side-steps.

---

### Post by undecim on 2009-11-06
You password is needed to decrypt the password you use to connect.

I personally prefer to replace Ubuntu's default network manager with wicd. The main difference is that wicd is set up system-wide, whereas Ubuntu's manager is set up on a per-user basis, but if you are the only one using the laptop, or don't care if other people on the laptop can connect to the same wireless networks as you, it works better.

to install, run in a terminal "sudo aptitude install wicd"

Once it installs, in the same terminal, type "killall nm-applet" to kill your current network manager, and the close the terminal. Press altf+f2 and type "wicd-client" to start your new network manager. 

You may also want to add "wicd-client" as a startup application.

If you want to go back to the old network manager, run the command "sudo aptitude install network-manager-gnome"

---

### Post by undecim on 2009-11-06
> **jbrown96 said:**
> Don't do this. Wicd is unnecessary. This doesn't solve the problem, it just side-steps.
With wicd, the wireless connects automatically when you boot (as long as you check "Automatically connect to this network")

How does that not solve the problem?

---

### Post by dox_drum on 2009-11-06
Thank you guys! I'll try the unlock... if it doesn't work then I'd try wick.

---

### Post by jbrown96 on 2009-11-06
> **undecim said:**
> With wicd, the wireless connects automatically when you boot (as long as you check "Automatically connect to this network")

How does that not solve the problem?

Network-manager is the officially supported. There's a reason why Ubuntu uses Network-manager and not Wicd. We shouldn't be telling new users to replace important system-level software for minor problems. Yes, there are certainly situations where Wicd would be a better choice, but it shouldn't be the default suggestion to new users. We don't want users getting over their heads right off the bat. I think that trying to keep Ubuntu vanilla is important when they first start. It's not a good idea to have them changing their system without understanding the consequences.

---

### Post by Giblet5 on 2009-11-06
> **jbrown96 said:**
> Don't do this. Wicd is unnecessary. This doesn't solve the problem, it just side-steps.

Wicd removes a buggy and poorly documented kluge (network-manager) with an interface that was designed by brain-damaged squirrels.

If that was ALL it did, I would agree. One can always use the conventional mechanism of /etc/network/interfaces ... which network-manager breaks. But, wicd does everything that network-manager does, except that it's documented, it works, and it follows proper UI guidelines.

That's more than a side-step; it's a leap from artificially-induced handicap.

---

### Post by P4man on 2009-11-06
wicd vs network manager aside, its worth explaining why the keyring password is being asked. 

dox_drum, ubuntu uses something called the keyring were applications can store passwords. This is used by emails clients, instant messangers, network managers and what not. When you are not logged in, those passwords are stored on your harddisk encrypted, The key needed to decrypt them is the keyring password.  apps can not decrypt it without you giving the key.

By default the keyring password is the same password as your log in password, though you can set a different one. If you log in, the keyring is opened and your passwords decrypted. Once open, apps will not have to ask your (keyring) password again, the passwords are available to them.

However if you change your login password, your keyring password is not changed, and therefore not opened on login. you have to open manually using your "old" password. If you want to change that, set your keyring password to the new account password in applications > accessoiries > passwords.

More likely however is that you enabled autologin. If you enable autologin, you dont need to give your password when you enter a session. A side effect of this is the keyring can not be opened (for obvious reasons your account and keyring password are not saved on your disk, you have to enter it).

If you dont like network manager or other apps prompting for the kreyring passwordm you have to
1) disable autologin and set same password for your account and keyring

OR

2) Do not use keyring for your network. Wicd I believe, does not use it. network-manager, if you click the  "enable this connection for all users"  will also not use the keyring (since other users with other passwords must be able to access it too). 

In the latter case you will still need to open the keyring for other applications if you use autologin.

---

### Post by jbrown96 on 2009-11-06
> **Giblet5 said:**
> Wicd removes a buggy and poorly documented kluge (network-manager) with an interface that was designed by brain-damaged squirrels.

If that was ALL it did, I would agree. One can always use the conventional mechanism of /etc/network/interfaces ... which network-manager breaks. But, wicd does everything that network-manager does, except that it's documented, it works, and it follows proper UI guidelines.

That's more than a side-step; it's a leap from artificially-induced handicap.

Are you serious? Dan Williams is a brilliant programmer, and Network-manager is a tremendous piece of work. Check out his blog. Almost all of the problems with network-manager are driver problems. Do any distributions use Wicd by default? I seriously doubt the Linux world would be following network-manager if Wicd was so much better. 

What's wrong with network-manger's UI? How is it undocumented? [http://projects.gnome.org/NetworkManager/developers/]("http://projects.gnome.org/NetworkManager/developers/")

Looking at the wikipedia page for Wicd, all of the criticisms of it are out-of-date. >     * Can distinguish between two access points with the same SSID but different MAC addresses
    * Does not have any GNOME dependencies, is environment independent
    * Provides a network list inside of the application window instead of as a dropdown menu from the tray icon
    * Will not connect to a wired network until instructed by the user
    * Will not connect to a wireless network until instructed by the user
    * Allows the use static DNS and/or static IP configuration for your wired and wireless networks

When you create a connection, there is a place to add the BSSID to differentiate connections. This is not done by default because most people use access-point roaming; however, I understand why you would not want to, but it's easy to configure.
Dan has a great blog post about #2 (about con-man). #3 is a personal choice, but I would rather have quick access to my network lists. there's also the "edit connections" window... #4 and #5 are the same thing... In "edit connections" there are settings to "connect automatically" to networks. #6 has been available since at least 9.04 and possibly earlier.

---

### Post by Giblet5 on 2009-11-06
> **jbrown96 said:**
> all of the criticisms of it are out-of-date.

That is entirely possible, and I'm sure Dan is a clever guy. But, so are the folks who wrote Microsoft Bob.

My anti-nm bigotry dates to Intrepid, where I tried to figure out how to define system-wide static IPs via ssh access. There was no documentation at all. None. So I did what anyone would do: I removed network-manager and manually configured eth0, eth1, eth2, and eth3 by hand, just like any ***professional*** Linux distro would do/does/will keep doing.

Then came Jaunty on a laptop. I tried wrestling with an ugly, retarded UI with some kind of listbox/spreadsheet-cell text entry system that can't even be navigated by keyboard alone. I'm surprised there aren't videos of someone trying to use that trash on FailBlog. My static IP config worked twice. Then came an update that wiped out the config. Problem was, one could no longer enter a static IP because clicking on the next spreadsheet-cell-tardwidget-in-a-listbox would clear the cell that had just been filled in.

That was when I discovered Wicd and I have never looked back. It just works. Beautiful, elegant, and it provides more features in a smaller footprint.

I gave nm another half-hearted try on Karmic. I saw the now-familiar spreadsheet-cell-tardwidget-in-a-listbox and clicked cancel, brought up a terminal window and replaced it with wicd, FTW.

Click your Network Manager Noodle o' Fail and try to configure static IPs on four interfaces. Just try. See that? Now try it with wicd. THAT is why I recommend wicd over network-manager.

Re your comment about drivers: When drivers are the issue, wicd won't fix it, so that argument is immaterial to this discussion.

If network-manager is superior to wicd, why do people move to wicd as soon as they learn of its existence? I imagine it's a mixed-bag combination of the above whining issues, coupled with the simple fact that wicd is better.

I'm glad to hear that network-manager has documentation now. I'll assume it covers non-gui configuration procedures: that was completely missing less than a year ago. Not that I care, since I have a solution that's easier to use.

And, if you haven't used wicd yourself, you better not talk to me about this any more: ignorant punditry makes me angry and I get snarky when I'm angry. ;)

---

### Post by P4man on 2009-11-06
> f listbox/spreadsheet-cell text entry system that can't even be navigated by keyboard alone

The retarded spreadsheet like interface when typing in static IPs and routes in network manager is *still* there. Its a prime example of a GUI FAIL. Unbelievable how long that bug or bogus gui has been around. Written by a genius or not, its retarded.

That aside nm does seem to work for me, but I concur that many people have seen their network issues (usually wireless) go away by switching to wicd, and i therefore also frequently recommend it as a solution.

---

### Post by dox_drum on 2009-11-06
Thank you again for all the information. You rule!

By the way, my actual configuration log in automatically... How do I change that option? So, perhaps the manager stop asking me permission for the key-ring.

[CENTER]Dox.[/CENTER]

---

### Post by dox_drum on 2009-11-06
> **dox_drum said:**
> By the way, my actual configuration log in automatically... How do I change that option? So, perhaps the manager stop asking me permission for the key-ring.

[CENTER]Dox.[/CENTER]

I found it, **System --> Administration --> Login Screen**.

:-)

[CENTER]Thank you![/CENTER]

---

### Post by markbl on 2009-11-06
I also had this problem where my laptop was asking me for the wpa password everytime I booted. In my case it is because I use auto-login.

Anyhow, I just worked out how to get around this. Not sure if this is posted elsewhere but run "nm-connection-editor" as your normal user and delete the wireless connection you want auto enabled. Then run "gksu nm-connection-editor" (i.e as root) and add the wireless connection again but this time tick the "Enable for all users" checkbox at the bottom. Also configure the wep/wpa password there of course. From then on the wireless will connect when your laptop boots and will just use the stored password.

---

### Post by GeneralSpecific on 2009-11-20
Wow...this thread got a little distracted away from fixing the problem.  The question wasn't "let's compare wicd and nm"  Not to offend anyone, it was interesting, but we need to focus on simple solutions to simple problems...

**[COLOR="Blue"]Thank you markbl[/COLOR]** :p

I did what you suggested and it worked fine. Though I did it directly through the "*system >network connections"* link.  And clicked edit.  It asked for access to the keyring.  I choose *"always allow"* and typed in my password a couple times.  

When I rebooted it connected immediately.  For some reason it created a new connection instead of editing the first one, but then I just deleted the old one.

It seems following your directions and making a new connection is the easiest way to fix this.

Working great now!

-Ryan

---

### Post by Mlemos on 2009-11-20
> **dox_drum said:**
> Hi people!

Since I install Karmic in my laptop, at any startup asks my for a key-ring password (or something like that) to connect to internet.

Is there any way to stop this? i. e., automatic connection or whatever.

Thank you!

Hello,

Just to share my experience. It started happening in my laptop after I have selected the System -> Administration -> Login Screen application to automatic log-in using my default user id.

I stopped it and now I am logging in with the password and it is not requesting the authentication for nm-applet anymore.

Does anyone can orient how to configure the keyring?

Best regards

ML

---

### Post by inearlygaveup on 2009-11-21
> **markbl said:**
> I also had this problem where my laptop was asking me for the wpa password everytime I booted. In my case it is because I use auto-login.

Anyhow, I just worked out how to get around this. Not sure if this is posted elsewhere but run "nm-connection-editor" as your normal user and delete the wireless connection you want auto enabled. Then run "gksu nm-connection-editor" (i.e as root) and add the wireless connection again but this time tick the "Enable for all users" checkbox at the bottom. Also configure the wep/wpa password there of course. From then on the wireless will connect when your laptop boots and will just use the stored password.

Thanks markbl - this worked for me also thanks to P4man for a clear description of the keyring application, its helped me. ):P

---

### Post by garvinrick4 on 2009-11-21
Going into the file that holds the keyrings as mentioned earlier and deleting the few that 
say keyrings and rebooting it will ask you for a new password put in nothing at all and say
ok. It will not ask you again. It was mentioned earlier and it works. Simple as all get out.
If your CPU is just hanging around the house and it doe's not one OK it is great. 
Take it into places where can be used by others do not do it just type your password.
What we will not do for one more tweak to save a stoke of a key. I believe which directory
and file are earlier post. See to lazy to go back and find in same thread.

---

### Post by vexorian on 2009-11-25
> **Giblet5 said:**
> Wicd removes a buggy and poorly documented kluge (network-manager) with an interface that was designed by brain-damaged squirrels.

If that was ALL it did, I would agree. One can always use the conventional mechanism of /etc/network/interfaces ... which network-manager breaks. But, wicd does everything that network-manager does, except that it's documented, it works, and it follows proper UI guidelines.

That's more than a side-step; it's a leap from artificially-induced handicap.
Sorry network manager is great, it is even friendlier than windows' way for wireless connections. I mean, before I wiped windows XP from my Acer aspire One I tried it and it was all so confusing. Network manager allows you to very easily have different local connections. Sorry but the necessity for a password is not a big deal.

---

### Post by MasterNetra on 2010-01-14
I know this thread is a couple of months old. But still the easiest way to get the keyring password to stop poping up with your autologin is to 

1. Left-click the network manager system tray icon.
2. Go to to edit connections.
3. Go to your wireless/wired connection(s) and check the "Available to all users" option at the very bottom (near cancel button). *Will require Authentication, so use your admin account.* 

ANd there you go. The keyring won't bother you for it/them any more.

---

### Post by bkratz on 2010-01-14
> **MasterNetra said:**
> I know this thread is a couple of months old. But still the easiest way to get the keyring password to stop poping up with your autologin is to 

1. Left-click the network manager system tray icon.
2. Go to to edit connections.
3. Go to your wireless/wired connection(s) and check the "Available to all users" option at the very bottom (near cancel button). *Will require Authentication, so use your admin account.* 

ANd there you go. The keyring won't bother you for it/them any more.

Covered in post #10

---

