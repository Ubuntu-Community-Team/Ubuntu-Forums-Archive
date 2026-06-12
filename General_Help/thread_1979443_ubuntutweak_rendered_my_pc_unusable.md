---
title: "ubuntutweak rendered my pc unusable"
date: 2012-05-13
forum: General Help
---

### Post by typos1 on 2012-05-13
I restored all my fonts to default values with ubuntutweak and now my pc is unusable. All menu boxes are tiny with no writing in, all drop down boxes are the same also there is no text anywhere apart from some window title bars and internet pages but because of the menu problem I cant even use them properly-I ve had to post this thread on my mob device because I cant see what I m doing on my pc cant even get as far as putting the thread title. 

I ve tried uninstalling ubuntutweak in recovery mode but that makes no difference nor does reinstalling it. For some reason a terminal wont open in normal mode and I cant see any writing any writing anywhere to do anything. In ubuntu tweak I just get icons now and only if I mouse over them its just a blank box. 

Is there anything I can do in recovery mode to restore system defaults?I ve tried logging in in gnome classic mode etc but everything is the same.

---

### Post by typos1 on 2012-05-13
I cant even read emails as they are all blank in thunderbird.

Please, please can some one suggest something to help me?

---

### Post by cottfcfan on 2012-05-13
I doubt whether resetting fonts to default could cause this.
Have you tweaked the theme or anything else?
The reason I asked is that I tried using a theme that wasn't compatible with 12.04 & saw a similar issue.

---

### Post by idoitprone on 2012-05-13
Are the tweaks only for you account or system wide?

Although I do not know anything about ubuntutweak. Does ubuntutweak uses root?
If it does then the tweak is system wide

If it does not then

All you have to do is reset your account to defaults

this involves removing hidden .files in your home directory

---

### Post by typos1 on 2012-05-14
I didnt change any theme, just reset fonts to defaults.

It is system wide-including if I logon in Gnome classic mode and all the other options on the login screen. I cant do things like delete hidden folders because I cant see anything !!

---

### Post by jadtech on 2012-05-14
i have read some where to becareful of ubuntu tweaks because it have several bugs apparently you have found  one of them .. 

have you tried to  create a new user account or loggin as guest to see if it changes things ???

---

### Post by typos1 on 2012-05-14
I thought the bugs were just in ubuntutweak on 12.04 and I m using 11.10 (wont let me upgrade to 12.04). Been using ubuntutweak for 2 years with no probs.

I ll try logging in as guest.

I managed to tell launchpad and theyve sent me a link to ubuntutweak 0.7.2.0 but I cant install it because software centre is totally blank apart from the software centre logo !

---

### Post by jadtech on 2012-05-14
> **typos1 said:**
> I thought the bugs were just in ubuntutweak on 12.04 and I m using 11.10 (wont let me upgrade to 12.04). Been using ubuntutweak for 2 years with no probs.

I ll try logging in as guest.

I managed to tell launchpad and theyve sent me a link to ubuntutweak 0.7.2.0 but I cant install it because software centre is totally blank apart from the software centre logo !

you could ttry to use the terminal to do the update..

---

### Post by typos1 on 2012-05-14
I have but terminals dont open anymore, or maybe they do but I just cant see them. Have to go into recovery mode instead. I un-installed and re-installed in recovery mode but it makes no difference. And if I go into ubuntutweak I cant see any text or menu boxes to do anything.

Logging in as guest gives me everything as default, pc usable now. 

Just got to work out how to restore defaults for my sessions . . .

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-14
try your tty ya know Ctrl+Alt+F1 (or 2...) 
Then of course you can Ctrl+Alt+F7 to get back to your screen.
You can try to delete the config for your user account (as was suggested before) in this mode.
That is probably the quickest and easiest thing to try.

---

### Post by jadtech on 2012-05-14
well you can create a new user with admin  will work the same and you can  do what needs to be done from there ad see things like should be ..

---

### Post by typos1 on 2012-05-14
I dont understand how that would help jadtech-I know how things should be, but I cant see anything to put them back to how they should be.

Treesofrightousness, I dont know how to delete the config for my user account.

And I m not sure how I can install the ubuntutweak update that launchpad sent me in tty mode either, or even if that would help as installing it and updating in recovery mode didnt help.

---

### Post by jadtech on 2012-05-14
> **typos1 said:**
> I dont understand how that would help jadtech-I know how things should be, but I cant see anything to put them back to how they should be.

Treesofrightousness, I dont know how to delete the config for my user account.

And I m not sure how I can install the ubuntutweak update that launchpad sent me in tty mode either, or even if that would help as installing it and updating in recovery mode didnt help.

setting up a ndew user account will get you normal desktop and stuff back till you can figure out how to delete  the configuration file ..

it is supose to be in your home folder but I sure dont find it in mine when I search I find at least 50 config file most having to do with keyboard set up ..

---

### Post by coffeecat on 2012-05-14
@typos, if you create a new account and log into that, you will be able to determine whether your system settings have been corrupted, causing these problems, or just your personal settings. Then you will be able to focus on what needs to be done or where. At the moment it is not clear whether there is a problem with system settings or personal settings.

Boot into recovery mode and choose drop to root shell. At the # prompt, enter this command:

```
adduser username
```

Substitute a suitable username for "username". You will be prompted (twice) for a password for the new account, and a few other questions. When you are returned to the # prompt, reboot with:

```
reboot
```

Now log in to the new account and tell us what you see. You will not have admin privileges (yet) with this new account, but we can attend to that later.

---

### Post by typos1 on 2012-05-14
I see, but I have logged in as a guest and everything is normal, its only in ubuntu, gnome, ubuntu 2D etc that things are messed up in.

---

### Post by coffeecat on 2012-05-14
> **typos1 said:**
> I see, but I have logged in as a guest and everything is normal, its only in ubuntu, gnome, ubuntu 2D etc that things are messed up in.

OK. Sorry I missed that before. In which case it's almost certain that it's your personal settings that are the problem and that deleting/renaming certain hidden files/folders will help. I'll post back with some suggestions in a minute or two.

---

### Post by coffeecat on 2012-05-14
To be honest I'm slightly at a loss as to which hidden folders need to be deleted/renamed so that their configuration files get regenerated to default when you next log in. If it was my system, I would simply fiddle about until I found the right ones, but that's not satisfactory for you.

What I suggest is that you do make a new account, and give it admin privileges. so that at least you have an account you can use as an admin with a GUI. All your individual app configs will be default until you adjust them, which is why I'm reluctant to tell you to delete hidden files in your original account just yet.

Boot into recovery mode and drop to root shell. Then these three commands:

```
adduser username
adduser username sudo
reboot
```

See my notes in my earlier post for what to do with the first command. The second adds the new account to the sudo group and, yes, this is correct. If anyone thinks that should be "username admin", that will work in 12.04, but in 12.04 the administrator group is now sudo to be consistent with upstream Debian.

Once you've logged into your new account, post the output of this command so that I can check that it's in all the groups it needs to be in.

```
id
```

---

### Post by typos1 on 2012-05-14
Sorry for delay.

I tried what you said. First I logged out, then went to recovery console, this was basically a terminal in the login screen. I thought I should go into recovery mode, so I shutdown and rebooted to recovery mode. Then I typed:adduser username 

I got (cant post output cos no copy paste etc, so had to take photo and type output):
adding user "username2"  . . .
adding new group "username2" (1001)  . . . 
groupadd: cannot lock /etc/gshadow: try again later.
adduser: " /usr/sbin/groupadd -g 1001 username2 returned error code 10. Exiting.

So I rebooted and now I cannot login as a guest, if I try to, after I press enter, the screen goes black for 2 secs then I get back to the login screen. Logging in in Gnome is also useless. I am now logged in in KDE mode!

This is an improvement as I can now access all my stuff and ubuntutweak hasnt affected anything using the KDE desktop (I can read everything and see all menus with KDE) only gnome and Unity.

---

### Post by coffeecat on 2012-05-14
You seem to be having a series of unrelated problems with your system. I must admit this is getting to be very puzzling.

First - the adduser commands should have run without incident. I've done something similar a few times myself without problem. Have a look at this bug report.

[https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/732864](https://bugs.launchpad.net/ubuntu/+source/qemu/+bug/732864)

The background is different from your situation, but the error messages are the same. Before you try to remove the lock files, boot into recovery mode -> root shell again and run this command:

```
ls /etc/*lock
```

If it lists the three files /etc/passwd.lock, /etc/group.lock and  /etc/gshadow.lock, then it should be safe to run the command:

```
 rm -f /etc/passwd.lock /etc/group.lock /etc/gshadow.lock
```

Whether that will enable you to run the adduser commands, I don't know. Something was probably already wrong for adduser username to fail.

> **typos1 said:**
> Logging in in Gnome is also useless. I am now logged in in KDE mode!

This is an improvement as I can now access all my stuff and ubuntutweak hasnt affected anything using the KDE desktop (I can read everything and see all menus with KDE) only gnome and Unity.

That's very interesting. So you can log into your main account in the KDE environment and everything is OK, but you can't now log into gnome at all? Have I understood correctly? As I said - a series of seemingly unrelated problems. Very strange.

---

### Post by typos1 on 2012-05-14
Yes, its affecting Unity also, dunno why its not affecting kde.

I ll just go into recovery mode and try what you suggested . . .

---

### Post by coffeecat on 2012-05-14
OK - but that will only help for creating a new account from the CLI. If it works. You can probably do that from KDE anyway and if you can log into KDE, you *might* be able to repair gnome from KDE.

---

### Post by typos1 on 2012-05-14
In KDE you cant even open a hard drive-evrytime I try it opens it with bit torrent (possibly because there is 1 torrent on it, but bit torrent does not contain this torrent when it opens) I simply cannot open it in KDE at all, it always opens it with bit torrent not nautilus, which is weird, is it a design fault or does it highlight another problem ?

Like I say, its not just gnome, its unity as well, or does unity use bits of gnome ? How can I repair gnome/unity from KDE if all the settings are fine in KDE ? Doesnt that mean that, even if I installed ubuntutweak from KDE what I do in it wont affect gnome or unity ?

Anyway I coded

ls /etc/*lock and got:

/etc/gshadow.lock   /etc/mtab.fuselock

---

### Post by coffeecat on 2012-05-14
> **typos1 said:**
> In KDE you cant even open a hard drive-evrytime I try it opens it with bit torrent (possibly because there is 1 torrent on it, but bit torrent does not contain this torrent when it opens) I simply cannot open it in KDE at all, it always opens it with bit torrent not nautilus, which is weird, is it a design fault or does it highlight another problem ?

I'm not sure I follow that but, yes, there is another problem that seems unrelated to the others you've explained.

> **typos1 said:**
> Like I say, its not just gnome, its unity as well, or does unity use bits of gnome ?

Unity uses most of gnome, or at least the gnome libraries and nautilus. Consider Unity as the Ubuntu shell for gnome. It's still gnome under the hood.

> **typos1 said:**
> How can I repair gnome/unity from KDE if all the settings are fine in KDE ? Doesnt that mean that, even if I installed ubuntutweak from KDE what I do in it wont affect gnome or unity ?

Your personal settings are hidden files and folders in your home folder, and you can see them in either gnome or KDE. Open a dolphin window in your home folder and do whatever you do in dolphin to reveal hidden files. It's probably ctrl-H as in gnome's nautilus, or from the dolphin view menu, I guess. Your .kde folder has your kde settings - leave that alone. Your gnome settings are in folders such as .gconf, .gnome2, .gnome2_private and so on. There are also some in sub-folders in .config. You can either delete or rename one or all of these folders to disable them. I prefer rename in this situation - .gconf -> .gconf.backup for example. When you next start gnome the hidden configuration files will be regenerated to their default condition. This may affect gnome applications as well as the desktop, depending on which files you delete. And that's as far as I can take you. It's difficult to tell which ones need changing with all the odd problems you are experiencing. All you can do is trial and error, unless someone else has a better idea.

> **typos1 said:**
> Anyway I coded

ls /etc/*lock and got:

/etc/gshadow.lock   /etc/mtab.fuselock

As I mentioned earler, this may not now help much. If you do delete the *.lock files, just delete the ones I listed earlier, not /etc/mtab.fuselock.

To be honest, if you encounter many more problems, it might be quicker and easier to backup your personal data and re-install. I know you may lose personal settings this way, but you're going to lose some or all anyway if you attempt to reset gnome's configurations by deleting/renaming hidden config files.

---

### Post by typos1 on 2012-05-14
Right, ok thanks, I ll have a think about what to do.

What I meant about the hard drive, is that I just wnat to open it with nautilus to see the contents,  but KDE wont open it, it just tries to do it with transmission, nautilus will not open the hard drive as a folder to let me view the contents. I m guessing its cos there is a torrent file on it, but it seems strange that KDE wont let nautilus open it.

Its KDE plasma by the way, if that makes any difference, not used any KDE stuff before, but I ve not come across any dolphin windows, how to I find them ?

---

### Post by coffeecat on 2012-05-14
Nautilus is the gnome file-browser, so you wouldn't normally see it working in KDE. Dolphin is the KDE file-browser and would have been installed when you installed KDE-plasma-desktop.

---

### Post by typos1 on 2012-05-14
I didnt install KDE plasma, its one of the login options, so must be part of the default OS settings, like having the option of gnome and gnome classic as well.

I ve gone into ubuntutweak in KDE and you can change nautilus settings, so it doesnt appear to be dolphin ? . . .

I d just like to be able to open my hard drive in KDE though, everytime I click on it, Transmission tries to open it !

Maybe theyve changed it and used nautlus and you arent usually a KDE user so havent realised? Not wishing to cause offence with that, just wondering why its got nautilus.

---

### Post by coffeecat on 2012-05-14
> **typos1 said:**
> I didnt install KDE plasma, its one of the login options, so must be part of the default OS settings, like having the option of gnome and gnome classic as well.

If you installed your system as Ubuntu and you have KDE as a login option, you must have installed one of kubuntu-desktop, kde-plasma-desktop or kde-standard packages. Ubuntu does not come with KDE components as default, neither does Xubuntu or Lubuntu. Only Kubuntu comes with KDE components as default, but Kubuntu doesn't come with gnome or Unity.

> **typos1 said:**
> 
Maybe theyve changed it and used nautlus and you arent usually a KDE user so havent realised? Not wishing to cause offence with that, just wondering why its got nautilus.

Nautilus is the gnome file-browser and is nothing to do with KDE. Dolphin is the KDE file-browser and is nothing to do with gnome. You can probably open nautilus in KDE (possibly dolphin in gnome) and use it, just as you can open and use many gnome applications in KDE, but it's a strange thing to do. Use the file browser that is native to your desktop environment.

---

### Post by coffeecat on 2012-05-14
Hmmm. Since your gnome seems to be quite broken, if you've been trying to use nautilus in KDE, that might explain some of your problems. Nautilus is deeply integrated into gnome just as Dolphin is deeply integrated into KDE. Hence my comment about using the native file manager. If gnome is broken then nautilus will probably be too.

It's too late for me to think about this further where I am, and I'm logging off soon, but something for you to think about.

---

### Post by typos1 on 2012-05-14
I have NEVER knowingly installed KDE on my system. I ve been using ubuntu for 3 years, I have installed once form a cd and upgraded to each subsequent new version via update manager, I ve ALWAYS used gnome and/or unity, this is the first time I have used KDE and I m only using it cos gnome and unity dont work.

I have various options on the login screen, including, gnome, gnome classic, gnome no effects, kde plasma, ubuntu, ubuntu 2D and recovery.

KDE is without question using nautilus as a file manager, I ve checked in ubuntutweak and you can tweak nautilus's settings and theres the shell icon.

The only thing I can think of is that something I ve installed has needed KDE repositories or something, if what you say is correct.

I have not been "trying" to use nautilus in KDE, KDE is using it ! All  I m doing is trying to access some folders by clicking on them and I used the word nautilus in my replies cos I assumed KDE used the same file manager.

I

---

### Post by coffeecat on 2012-05-14
> **typos1 said:**
> 
The only thing I can think of is that something I ve installed has needed KDE repositories or something, if what you say is correct.

You will indeed install quite a bit of the KDE base libraries if you install KDE apps in Ubuntu/gnome. I routinely install things such as okular and k3b whenever I do a fresh installation of Ubuntu, and these bring in quite a few KDE dependencies. But these sorts of apps do not usually bring in enough of KDE for it to be a login option. So something that you've installed in the last few years has brought in enough of KDE for you to be able to log into the KDE desktop. 

Anyway...

> **typos1 said:**
> I have not been "trying" to use nautilus in KDE, KDE is using it ! All  I m doing is trying to access some folders by clicking on them and I used the word nautilus in my replies cos I assumed KDE used the same file manager.

Once you've opened whichever file manager it is, you should be able to identify it from the help menu -> about. I'd be interested to hear which it is! :)

---

### Post by typos1 on 2012-05-14
Hmmm, whatever folder I click on, transmission is trying to open it, even my home folder!

In KDE, I get what I assume is the default desktop background , wich is empty. I cannot get any folders to open, ransmission tries to open any folders.

I opened a downloaded file by right clicking and using "open folder" and this opened my desktop from gnome/unity, complete with my background and files on it. And this is now the desktop in KDE, just opening it seems to have set the complete desktop from gnome as my desktop. Whilst it was open as a folder, I clicked on help, there was no "about" and it was "KDE desktop effects". 

Firefox has all my bookmarks same as gnome/unity, by the way and all my open tabs appeared in firefox from when I was last using gnome and unity.

When I opened some of the folders the background was a flash animation from a webpage that is open. 

Very weird.

---

### Post by TREESofRIGHTEOUSNESS on 2012-05-15
Firefox retained those things because they are your personal settings....  SO... we will back up the things we are removing by simply changing them
```

mv ~./config ~/BACKUPconfig

```

You may need to 'delete' other 'hidden' folders as well... 
just apply the same method as above..  

Oh... if you can open a terminal you can always type 
```

nautilus

```
to bring up nautilus

---

### Post by coffeecat on 2012-05-15
In order to get a handle on what you are describing, I installed the package kde-plasma-desktop in one of my systems and at the login screen I'm offered "KDE Plasma Workspace" as one of the login options. Choosing this takes me to a seemingly fully-functional, albeit spartan, KDE desktop.

> **typos1 said:**
> Hmmm, whatever folder I click on, transmission is trying to open it, even my home folder!

To be able to click on a folder, you need to have a file browser open, so where is the folder that you are clicking on? Somehow Transmission has been associated with opening folders. If you are seeing the folder in Dolphin (see below), then right-click on the folder -> open with -> dropdown the list under settings, tick the remember application box and choose dolphin from the dropdown list.

I somehow doubt you're using nautilus in KDE. To do so, you'd need to run it from a terminal and then it looks really weird with the Ubuntu orange folder icons against the blue-grey KDE colour theme. Unless you've managed to get part of gnome as a widget in KDE (see below).

> **typos1 said:**
> In KDE, I get what I assume is the default desktop background , wich is empty. I cannot get any folders to open, ransmission tries to open any folders.

Yes, the default KDE desktop is spartan. In order to get a conventional desktop on which you can store files and things, you have to create a widget.

Go to bottom left and click on the blue 'K' icon. You should see dolphin as one of the choices. Open it. Is this what you see when you are clicking on folder? The default colour scheme for dolphin is blue for folders (orange for folders in Ubuntu's nautilus).

> **typos1 said:**
> I opened a downloaded file by right clicking and using "open folder" and this opened my desktop from gnome/unity, complete with my background and files on it. And this is now the desktop in KDE, just opening it seems to have set the complete desktop from gnome as my desktop.

Not sure what's happened here. Perhaps you managed to create a widget with elements of gnome on your KDE workspace.

> **typos1 said:**
>  Whilst it was open as a folder, I clicked on help, there was no "about" and it was "KDE desktop effects". 

If you open a folder in dolphin, you see the contents of the folder but you are still in dolphin - just as with any file manager. If you click on the toolbox icon on the right -> help, you'll see "About Dolphin". So I don't know where desktop effects has come from.

> **typos1 said:**
> Firefox has all my bookmarks same as gnome/unity, by the way and all my open tabs appeared in firefox from when I was last using gnome and unity.

Yes - that's fine. The firefox settings are in a hidden folder called .mozilla in your home folder and accessible from both gnome and KDE. The only difference you should see is the theming. At least your firefox settings haven't been damaged by whatever is going on.

> **typos1 said:**
> When I opened some of the folders the background was a flash animation from a webpage that is open. 

Curious. I don't want to complicate things, but if you go back to the KDE menu bottom left, you'll see Web Browser (Konqueror) as one of the choices. Although it is used as a web browser, it is a perfectly functional file browser as well, and used to be the file browser in KDE3 before the KDE people developed dolphin for KDE4. I wonder if that's anything to do with this. As you see, you have a number of choices for browsing files and opening folders in KDE, so this might help.

By the way, what I'm describing is in 12.04. I can't recall whether you mentioned which release you are using. It must be 11.04 or later because you mention Unity.

---

### Post by typos1 on 2012-05-15
The file was in transmission, I clicked on "open folder".

If I right click on a folder I get "home" which is greyed out, "add to desktop" and "add to panel", there are no other options.

I ve tried changing what opens files using ubuntutweak, but I cant cos nautilus is the only option.

I have no "K" icon. I did have a strange overstylised squiggle which may have been a "K" yesterday, but not now.

I  cant get into dolphin ! I got into "KDE desktop effects" as I posted yesterday, but cant get into dolphin.

Iam familiar with the .mozilla folder.

I have heard about Konquerer and that you can open files with it as well. Cant find it though (by the way firefox can also open files).

I m using 11.10, by the way, it wont let me upgrade to 12.04, it says it failed to fetch some (old) repositories, says older ones have been used instead, but when I click on ok it starts restoring the system to its original state and doesnt complete the update. Although thats the least of my worried at the moment !

On the bug page for ubuntutweak in launchpad, I ve been told to code 

"mv ~/.config/dconf ~/.config/dconf.bak"

in a terminal, to restore my settings to default. But I cant find a terminal. I ve got Xterm and uxterm, but the script in them when I open them is:

username@username:~desktop/Documents$

I ve not come across the documents bit before, so thought I d get advice before I try and use them. I ve tried putting "terminal" and "konsole" in search but nothing comes up.

By the way, I always have the "view hidden folders" box checked in nautilus.

---

### Post by coffeecat on 2012-05-15
Well - you said before that you never installed a package to install the KDE desktop, and I believed you. Even though you have a login choice for KDE somehow, it really does seem as though you do not have a complete and functional KDE desktop. And since you can't open a terminal, you are very limited in the options open to you.

Last thing - click on the "overstylised squiggle" at bottom left. Does that open the KDE menu? If it does, you should be able to find all the applications, including terminal and dolphin, there. If not then, sorry, I have nothing further to offer, but perhaps someone else does. It does seems as though the settings in your system are very damaged. In theory, it could be fixed. In practice, as I said before, it might be quicker and easier to to a fresh install.

---

### Post by typos1 on 2012-05-15
I havent ever specifically installed KDE. Before unity came out I used AWN and later Cairodock, was never fully happy with them, so used unity and cardapio (I hate dash so much) after unity came out. I think AWN and Cairodock may have installed some KDE stuff. 

As I said in my last post, the stylised squiggle has gone now, but was there yesterday.

Just looked around again and I think it is for nepomuk. But I do get the arrow thing which is for apps/places. This is where I can get to folders (but not get into them) and where the xterm an uxterm windows are. What are they by the way ?-terminals for desktop and docs or something ?

I can also confirm that I am DEFINATELY using nautilus in KDE, I found "about" and checked.

---

### Post by typos1 on 2012-05-15
Well I tried typing what launchpad told me to type in a terminal, in recovery mode. ( mv ~/.config/dconf ~/.config/dconf.bak )

It didnt work. 

Dont know if this is cos I was in recovery mode, or because (and I know this sounds silly) I couldnt type the squiggly line in the middle (like this ~ ), it would only go higher, if you see what I mean, ie not as low as an underscore, or in the middle like this ( ~ ) but at the top of the space, ie the opposite to an underscore. I hope I m making myself clear. As you can see from this post " ~ " appears in the correct place when I m logged in in a GUI mode, but not in recovery. 

Does this make any difference ? 

Thanks

---

### Post by coffeecat on 2012-05-15
~ is the tilda symbol and is shorthand for your home folder. Let's assume your account name in Ubuntu is typos1, then you will have a folder typos1 in the home folder, and the path to your home folder would be /home/typos1. When you use ~ in the terminal it gets interpreted as the path to your home, so if you are logged in a typos1, then ~ = /home/typos1. However, in the recovery console you are logged in as root and the ~ sign would be interpreted as root's home, not yours, and the config files you are trying to rename are in your home, not root's.

So if you are in recovery mode, you would need to type the full path with the mv command, that is:

```
mv /home/typos1/.config/dconf /home/typos1/.config/dconf.bak
```

Obviously, change typos1 to whatever your account name is in Ubuntu.

Don't worry that the ~ was being rendered oddly in the recovery console. If you are using the ~ key, then the correct character code is being registered. But as you can see the use of ~ in recovery console doesn't help you.

---

### Post by typos1 on 2012-05-15
Right, I see.

Well, I also tried it in the xterminal that also had documents in the address, rebooted and I ve got everything back !!

Well, mostly, there are duplicate icons in unity and the ones I had added there myself have disappeared.

Plus I ve had to add location to weather applet again and my desktop pic has been replaced with default, (easily fixed obviously).

After upgrading to the first version with unity, I couldnt find how to customize ubuntu using appearance, you know like fonts and background colours etc. 

A few days back I did manage to find how to alter those things, I m not sure where though. It might have been ubuntutweak, but I m not overly sure. The reason that I had all these probs was because I had altered a few of these settings in where ever it was I found out where I could and wasnt happy with the typeface-the one I had picked was very thin and spidery (a bit like the default Windows XP typeface). So I tried doing it in ubuntutweak and well, you know what happened. 

Well, whilst everything is back, I ve still got that damn typeface !!

I really wish they could have made unity using the classic ubuntu menu, with the list of applications catergories, preferences and administration, had the option to put that in unity instead of dash.

It was so intuitive, changing everything about and regrouping things (like replacing admin with system settings and control center just makes things harder to do (even 18 months on) and as I ve got cardapio with classic style menus on AND unity it can get very very confusing trying to find out where everything is, with old and new styles combined. 

I suppose I should go back to AWN as what I really wanted unity to do was replace all the panels with one panel on the left for everything, you can do that with gnome and AWN.

And I still cant upgrade as 4 back ports from Jaunty cause update manager to put everything back as it was and abort the upgrade. 

Thanks for all the help, by the way ! :)

---

