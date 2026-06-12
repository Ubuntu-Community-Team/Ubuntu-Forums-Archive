---
title: "Problem with booting up"
date: 2010-05-04
forum: General Help
---

### Post by aewrfh on 2010-05-04
[I][B][SIZE=4][COLOR=Lime]note: acct and acct2 are not the actual account names.

I spent a long time figuring out this ubuntu problem on my own and decided to share it with the ubuntu users out there. I will give a summary of what had happened and what I had done to resolve it. I did a lot of complicated account password changing as well. I wanted to get rid of the login keyring thing.

I had tried messing around with some of ubuntu's settings when I first installed 10.04 Lucid Lynx.
I changed settings in: System>>Administration>>Users and Groups, and System>>Administration>>Login Screen.
I got terrible results, but ended up solving it on my own.

The first account I had was named "acct".
I had an issue with the keyring always needing to be unlocked, meaning I had to type in a password twice.
I did not like this.

So I decided, why not delete this "acct" account and make a new one that I can use?

I made a second user account called "acct2". I messed around a lot with the settings, just to see what would happen and what would work.

I tried to cut out some of the files that were in the other account, the account "acct", while I was in user account "acct2". I could not because I did not have the rights to do it.

I realized I had to change those files to shared. I logged back into the other account "acct", which was an administrator account. I made them all shared files.

Next, I went back into acct2, then cut all the files out of acct that I needed, then I deleted the home folder for acct.

This is probably where the problems all started. I always start with the purple screen and have no choice to log into my usable acct2 account and have to wait 7 minutes to get that option to do so.

When I rebooted, the screen popped up a couple windows reporting errors to me:
*Could not update ICEAuthority file /home/acct/IceAuthority
*There is a problem with the configuration server (/user/libgonf2-4/gconf-sanity-check-2 exited with status 256)
*Nautilus could not create the following required folders: /home/ki/Desktop,
/home/acct/.Nautilus
*Before running Nautilus, please create these folders or set permissions such that Nautilus can create them.

Next, I had a purple blank screen(the Ubuntu default desktop background). I just waited like 7 minutes and the screen turned black and upon pressing a key, a log-in window shows. I can attempt to enter into either account.

I try to log into the acct2 account. Then a more colorful log-in menu shows up, rather than the plain one that I had opened just previously.

I look at acct in the menu and I see that it's logged in.

While in acct2, I had tried to delete "acct" account in: System>>Administration>>Users and Groups. I could not do that because, acct was still logged in. Whenever I try to "log in" into acct, I get the frozen blank purple background and I can't do anything much. I can't log out. I can use ctrl+alt+del to shutdown or restart, but I'm not allowed to log out. I had been puzzled.
When I do restart or shutdown and try booting in again, it's the same purple screen with the acct account.

Logging back into the acct2 account, I unchecked "don't ask for password on login" in: System>>Administration>>Users and Groups. I created acct folder(home folder), which was missing. This was just me experimenting to see what works.

I used my cell phone's Internet to look up some help on what to do. I considered using the terminal command: gnome-session-save --kill which would log you out. 

I took note of this terminal command:w,  which tells which users are logged in at that moment.

I started the computer again, rebooting, many times. I went into ubuntu recovery option at the grub bootloader. I messed around a lot. I used the terminal version of the accounts while in that mode. I used startx on both accounts. It worked for acct2, but not acct. When I used startx on acct, I got "unable to start cannot open display" shown to me in a window. I found out "logout" is also a command for ubuntu terminal.

I went back in acct2. I got to know about some extraneous knowledge along the way, but are helpful to know, such as the four states of session types, the KDE GUI doesn't work with Ubuntu, but it works on Kubuntu, and that someone on a forum said that it is never safe to log into root account.

4 types of default session types:
1)GNOME
2)Xterm(failsafe session w/ only xterm)
3)failsafe GNOME
4)KDE (The K Desktop Environment)

Inside of Administrator account acct2, I went in System>>Administration>>Login Screen, then made some modifications. I checked the radio button: "show the screen for choosing who will log in". This is very important for avoiding the 7 minute purple frozen screen. I didn't ask for a password upon log-in for acct, so that is why it came to that desktop screen. It's just the Desktop just won't start up and purple is all you get. So I automatically, from now on, just see a log-in menu from the start, even if acct is still "logged in".

I found that there was an Xterm session and I explored into that. I think, but I don't remember too well, that I logged into acct with Xterm, then either entered gnome-session-save --kill, or just "logout". 

I think soon after, the acct account was no longer logged in and I was able to delete the account in: System>>Administration>>Users and Groups, inside of the acct2 user account.

This fixed my problem.




CONCLUSIONS:

*Be careful about sharing files in Ubuntu, like cutting and pasting some files/folders out of the acct account, the Home folder. Some of them are required for booting into that account.

*Xterm doesn't require a GUI.

*I thought that I could snatch the folder out of that acct account first, then, delete the account. It didn't work like that. It just stays logged in when you try to switch out of one session and log into another. I can be logged into 2 accounts at the same time. This could be bad considering you make it so that you can't use the original account because it's missing some files/folders, so you can't log out of that specific user account normally any more.

*I couldn't boot up into the GUI of the account, acct, which auto starts when you boot up. This account can't be deleted until you are logged out of it, which seems impossible to do because when you try using it by going into it, it won't let you log out because it's a frozen purple screen(desktop background).

* I could have instead just simply used an external drive and cut and pasted my desired files into it, while inside the acct account, which held the files, in the first place. Instead, I accessed those files from another user account and took a greater risk.

* I am glad and satisfied that I have fixed this problem for myself. I hope this can help other users out there who may have similar problems, help people avoid this, or people who just would like to know more about how Ubuntu works.

[/COLOR][/SIZE][/B][/I][http://www.flickr.com/photos/aewrth/4579140577/](http://www.flickr.com/photos/aewrth/4579140577/)
[http://www.flickr.com/photos/aewrth/4579770714/](http://www.flickr.com/photos/aewrth/4579770714/)
[http://www.flickr.com/photos/aewrth/4579877342/](http://www.flickr.com/photos/aewrth/4579877342/)
[I][B][SIZE=4][COLOR=Lime] [IMG]http://www.flickr.com/photos/aewrth/4579140577/[/IMG]

[/COLOR][/SIZE][/B][/I]

---

### Post by linuxman94 on 2010-05-04
Please use the default text color and size down your text.  It makes it a lot easier to read.

---

