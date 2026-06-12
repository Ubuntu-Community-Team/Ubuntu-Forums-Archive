---
title: "GOOGLE chrome search bar popup grr"
date: 2010-07-10
forum: General Help
---

### Post by cake nom nom on 2010-07-10
how do i get rid of this little box everytime i try to hit ctrl+a to highlight the whole search bar to type somthing in or double click to highlight 

a little popup box comes up asking me if i want to open with fire fox or send url or open with opera or modzilla its mad annoying i cant find anywhere how to get rid of it can anyone help? heres a video i took to show what it is

[http://www.youtube.com/watch?v=4LMyWfIqup0](http://www.youtube.com/watch?v=4LMyWfIqup0)

---

### Post by robsoles on 2010-07-10
I think your mouse is broken - can you get alternate mouse and try what happens in similar circumstance?

this is my edit: I ask because this is what I perceive as intended behavior for 'context sensitive menu' otherwise known as 'right-click-menu'.

---

### Post by cake nom nom on 2010-07-10
thanks for the reply but as i said previously, when i hit ctrl a it happens as well as when i double click i don't think its my mouse

---

### Post by robsoles on 2010-07-11
Does it do the same thing good old firefox?

A little digging didn't show me where I can turn such a feature on 'easily' within my system, I even installed chromium browser and had a squiz at their options - nothing simple, that's fairly sure.

If it doesn't do it in any other program then I can suggest that scrubbing all settings, add-ons and related from Chrome will very likely fix it - lemme know if you want to pursue that.

---

### Post by cake nom nom on 2010-07-11
> **robsoles said:**
> Does it do the same thing good old firefox?

A little digging didn't show me where I can turn such a feature on 'easily' within my system, I even installed chromium browser and had a squiz at their options - nothing simple, that's fairly sure.

If it doesn't do it in any other program then I can suggest that scrubbing all settings, add-ons and related from Chrome will very likely fix it - lemme know if you want to pursue that.



__

1. i dont want to turn it on i want to turn it off, and it's default settings on google chrome i think.. no other program or addon affects it 

here is a better video of my problem 

[http://www.youtube.com/watch?v=15D9Nh6dusE](http://www.youtube.com/watch?v=15D9Nh6dusE)

---

### Post by robsoles on 2010-07-11
> **cake nom nom said:**
> __

1. i dont want to turn it on i want to turn it off, and it's default  settings on google chrome i think.. no other program or addon affects it  

...



If I could find where to turn it on then I could tell you where to turn it off - I thought that spoke for itself...

It is not a default setting in Google Chrome, or at least I couldn't get it to do what you say it does for you by doing the things you say does it - that is why I looked for where I could possibly enable/'turn on' what you are complaining about!!!


> **cake nom nom said:**
> ...  

here is a better video of my problem 

[http://www.youtube.com/watch?v=15D9Nh6dusE](http://www.youtube.com/watch?v=15D9Nh6dusE)


It isn't possible to tell what you are clicking or pressing to make that happen on your display because the mouse and the keyboard activity aren't revealed in the video.

Would you like to try completely purging the settings that Google Chrome is using? (I can walk you through that but I'm not posting how (again) without you saying it is what you really want - all bookmarks, history and cache will be trashed if this is pursued.)

---

### Post by cake nom nom on 2010-07-11
ijust hit ctrl + a 

select all or highlight all on the search bar

---

### Post by robsoles on 2010-07-11
Like I said, I did those to chromium-browser freshly installed on my system and it wouldn't do what you say yours does.


If this is the only program exhibiting the problem then purging it's settings while it isn't running (at least) and perhaps going as far as to uninstall and re-install it will probably fix the problem - at least it would stop me harping about that as a solution and get me to move on to other things that may provide a solution.

---

### Post by cake nom nom on 2010-07-11
do you think its beacuase i have different browsers installed? i have so many settings customized on my chrome to have it not fixthe problem uhghhh any way i dont think its a bug or somthing  it because i installed a diff chrome from ubuntu tweak and it does the same thing

---

### Post by robsoles on 2010-07-12
I very much doubt it is because of the different browsers you have installed.


Your settings will be retained if you uninstall using the GUI so that when you reinstall you will still have all the bookmarks, settings etc etc that you built up over time - this also means that if it is some user setting I haven't found by a little digging then it will persist through reinstall after reinstall... The standard way of uninstalling in the terminal also retains all your settings - it is possible to remove all settings etc by (rudely) deleting a specific folder in your home directory without actually uninstalling chromium-browser and there is an apt-get (or aptitude) command that should remove your settings but I find it best to check that the folder has been emptied if not removed after running apt-get (or aptitude) using the 'purge' command.

[COLOR=Red]**Don't just open terminal and type anything in until a little more info comes your way!!!**[/COLOR]

Here is an alternative for you to try: Create yourself a new user on your computer there and log in as this new user, open chromium-browser and check if this behavior happens to your new user you have logged in as.


If it doesn't happen the same then what I am suggesting about purging your settings should easily work a treat, if it does happen just the same then it points us in a new direction to think of.

---

### Post by cake nom nom on 2010-07-14
> **robsoles said:**
> I very much doubt it is because of the different browsers you have installed.


Your settings will be retained if you uninstall using the GUI so that when you reinstall digging then iyou will still have all the bookmarks, settings etc etc that you built up over time - this also means that if it is some user setting I haven't found by a little t will persist through reinstall after reinstall... The standard way of uninstalling in the terminal also retains all your settings - it is possible to remove all settings etc by (rudely) deleting a specific folder in your home directory without actually uninstalling chromium-browser and there is an apt-get (or aptitude) command that should remove your settings but I find it best to check that the folder has been emptied if not removed after running apt-get (or aptitude) using the 'purge' command.

[COLOR=Red]**Don't just open terminal and type anything in until a little more info comes your way!!!**[/COLOR]

Here is an alternative for you to try: Create yourself a new user on your computer there and log in as this new user, open chromium-browser and check if this behavior happens to your new user you have logged in as.


If it doesn't happen the same then what I am suggesting about purging your settings should easily work a treat, if it does happen just the same then it points us in a new direction to think of.


dang i logged into a guest account & it didn't do the problem your absolutely right

---

### Post by robsoles on 2010-07-14
So, will you take shortest path to being rid of the problem under your own login (scrub settings and stuff) or do you just gotta know what caused it to become like that?

---

### Post by cake nom nom on 2010-07-15
what ever is easier  for you i guess :-k

---

### Post by robsoles on 2010-07-15
Shortest path is actually easiest in this case but will lead to you losing your bookmarks, history and saved passwords.

If not worried about losing those then open a terminal and type
```
sudo apt-get purge chromium-browser
```

If that reports errors please post the errors back to this thread, otherwise may as well use terminal to reinstall
```
sudo apt-get install chromium-browser
```

Again, if errors are reported then post them back here. If no errors then test the browser again and let me know if that ditched the problem or not - if the problem persists through that I will post which folders are created in your home directory by chromium-browser and how to safely remove them.

---

### Post by cake nom nom on 2010-07-15
nah not worried about that stuff

---

### Post by robsoles on 2010-07-15
So how did following the 'code' instructions in my post #14 go?

---

### Post by cake nom nom on 2010-07-15
first code: 

drnomnomcake@drnomnomcake-laptop:~$ sudo apt-get purge chromium-browser
[sudo] password for drnomnomcake: 
Sorry, try again.
[sudo] password for drnomnomcake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  chromium-browser* chromium-browser-inspector* chromium-codecs-ffmpeg*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 44.3MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 186219 files and directories currently installed.)
Removing chromium-browser ...
Purging configuration files for chromium-browser ...
Removing chromium-browser-inspector ...
Removing chromium-codecs-ffmpeg ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...

2nd code

drnomnomcake@drnomnomcake-laptop:~$ sudo apt-get install chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-inspector chromium-codecs-ffmpeg
Suggested packages:
  chromium-browser-l10n
The following NEW packages will be installed:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.7MB of archives.
After this operation, 44.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package chromium-browser-inspector.
(Reading database ... 185942 files and directories currently installed.)
Unpacking chromium-browser-inspector (from .../chromium-browser-inspector_5.0.375.86~r49890-0ubuntu0.10.04.1_all.deb) ...
Selecting previously deselected package chromium-codecs-ffmpeg.
Unpacking chromium-codecs-ffmpeg (from .../chromium-codecs-ffmpeg_0.5+svn20100406r43776+43984+43918-0ubuntu1_i386.deb) ...
Selecting previously deselected package chromium-browser.
Unpacking chromium-browser (from .../chromium-browser_5.0.375.86~r49890-0ubuntu0.10.04.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up chromium-browser-inspector (5.0.375.86~r49890-0ubuntu0.10.04.1) ...
Setting up chromium-codecs-ffmpeg (0.5+svn20100406r43776+43984+43918-0ubuntu1) ...
Setting up chromium-browser (5.0.375.86~r49890-0ubuntu0.10.04.1) ...

then i opened up google chrome again & it takes me right back to this thread & my bookmarks are all still there problem still there, so i do the first code again

drnomnomcake@drnomnomcake-laptop:~$ sudo apt-get purge chromium-browser
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  chromium-browser* chromium-browser-inspector* chromium-codecs-ffmpeg*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 44.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 186219 files and directories currently installed.)
Removing chromium-browser ...
Purging configuration files for chromium-browser ...
Removing chromium-browser-inspector ...
Removing chromium-codecs-ffmpeg ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
drnomnomcake@drnomnomcake-laptop:~$ 

& my google chrome is still in my applications & the problem persists 

what should i do now?

---

### Post by robsoles on 2010-07-15
It is not too much a surprise to me that the 'purge' command didn't work - it relies on the people who made software in question taking a step that I didn't think those guys took.

It is a surprise to me that the application persisted through an uninstall!

Try this way:
[B]Using the GUI/Desktop, open your home folder - usually the top item under the 'Places' menu.

Press '[CTRL]-[H]' to reveal hidden files and folders.

Locate '.config' and double-click it or open it whichever way you like.

Find 'google-chrome' inside that and select/highlight it. Press [Shift]-[Delete] on keyboard, confirm your choice.[/B]


Re-open chromium-browser (if it doesn't open now then just re-install it using whatever method you like) and check if it has the 'problem' anymore - if it does let me know and I will (be stunned and) have another go at it for you!

---

### Post by cake nom nom on 2010-07-15
okay so i deleted the folder, then i tried to open a new session under apps > internet > google chrome & it asked me if i wanted to import settings from modzilla i said no, then it asked me to make default browser i said no & the problem still purists

---

### Post by robsoles on 2010-07-15
There has to be something else chromium-browser creates in your home folder that I haven't spotted from here at work.

I will have to check harder when I get home tonight - it's about 5 or 6 hours before I can get a better look at it.

Another question I would like to ask you is if you only installed chromium-browser from apt (including 'synaptic' and ubuntu software centre) or if you got it from somewhere else?

---

### Post by cake nom nom on 2010-07-16
i think i got it from the website

---

### Post by robsoles on 2010-07-16
> **cake nom nom said:**
> i think i got it from the website

Then it cannot be removed by apt.

can you find the original file(s) you downloaded from the website?

tell me the full file name(s) if you can.

---

### Post by robsoles on 2010-07-16
Hey, right click your 'Applications' menu for me and select 'Edit Menus' from the list there.

In the menu editor find the launcher you've been using for this browser and then choose 'Properties' - when the new little window opens up look in the 'Command' box and post back to me what is written there please.


We can probably delete this launcher, leave the stuff their own installer put on your system and re-install from the Canonical Repository and make it look very much like your problem is fixed but I wouldn't mind taking a stab at removing the files their installer put on your PC first.

---

### Post by graphixfx on 2010-07-16
is chrome your default browser?

---

### Post by cake nom nom on 2010-07-16
> **graphixfx said:**
> is chrome your default browser?

I it was then i reinstalled it & now its not the problem still exists[]("http://ubuntuforums.org/member.php?u=1004749")

hey robsoles i look at my application menu and i have to different kinds of google crome, the blue one is the one from the ubuntu software center the one i belive you had me install through the install & the other is different it is the one i have been using here is a screen shot 

[http://i25.tinypic.com/66euk5.png](http://i25.tinypic.com/66euk5.png)

however they both have the problem, when i did the install you told me to do the blue one went away then it came 

however i  could not locate the original file i downloaded from the website

---

### Post by cake nom nom on 2010-07-16
> **robsoles said:**
> Hey, right click your 'Applications' menu for me and select 'Edit Menus' from the list there.

In the menu editor find the launcher you've been using for this browser and then choose 'Properties' - when the new little window opens up look in the 'Command' box and post back to me what is written there please.


We can probably delete this launcher, leave the stuff their own installer put on your system and re-install from the Canonical Repository and make it look very much like your problem is fixed but I wouldn't mind taking a stab at removing the files their installer put on your PC first.


/opt/google/chrome/google-chrome %U

---

### Post by renkinjutsu on 2010-07-16
I don't think it is a chrome problem, but look here to see if there's anything that might contribute [chrome://extensions]("chrome://extensions") and then disable it.

Also, it looks like it might have something to do with your desktop environment (not sure).

open up gedit and type in ```
http://www.facebook.com
``` and do the same... does the same thing happen?

---

### Post by robsoles on 2010-07-16
> **renkinjutsu said:**
> I don't think it is a chrome problem, but look here to see if there's anything that might contribute [chrome://extensions](chrome://extensions) and then disable it.

Also, it looks like it might have something to do with your desktop environment (not sure).

open up gedit and type in ```
http://www.facebook.com
``` and do the same... does the same thing happen?

We've long established that it only happens in cakenomnom's copy of chromium-browser.


@cakenomnom: It is well worth putting 'chrome://extensions' (don't put apostrophes) into the address bar of chromium-browser and seeing if you can find anything that sounds like it might do that - for renkinjutsu's satisfaction there is no harm doing the test in gedit, maybe you are wrong about it only being chromium-browser after all.

---

### Post by cake nom nom on 2010-07-16
chrome://extensions says i dont have any extensions

---

### Post by renkinjutsu on 2010-07-16
Cake, you never mentioned whether or not you can replicate the problem with software other than Chrome. Did you try the same thing in Firefox or Gedit?

The previous test (creating a new user) only rules out a user specific problem. And the deletion of ~/.config/google-chrome rules out a chrome specific problem. So i thought this "feature" might actually be system wide, for your user of course. Could be some sort of GTK or GNOME option.

---

### Post by robsoles on 2010-07-16
> **cake nom nom said:**
> ...

1. i dont want to turn it on i want to turn it off, and it's default settings on google chrome i think.. no other program or addon affects it 

...[/url]

Yep, I spose that isn't really all that clear as to whether or not it happens in other programs.

Will you please do the test this guy suggested so we can get on with fixing this:
> **renkinjutsu said:**
> ...

Also, it looks like it might have something to do with your desktop environment (not sure).

open up gedit and type in ```
http://www.facebook.com
``` and do the same... does the same thing happen?

---

### Post by cake nom nom on 2010-07-16
> **renkinjutsu said:**
> Cake, you never mentioned whether or not you can replicate the problem with software other than Chrome. Did you try the same thing in Firefox or Gedit?

The previous test (creating a new user) only rules out a user specific problem. And the deletion of ~/.config/google-chrome rules out a chrome specific problem. So i thought this "feature" might actually be system wide, for your user of course. Could be some sort of GTK or GNOME option.


does not happen in firefox or gedit only chrome ):

---

### Post by renkinjutsu on 2010-07-16
hmm.. it could be a chrome option. I just checked the chrome releases blog and found that they've released a new version (But it is a Dev channel update). Are you on the Dev channel or the Stable channel of google chrome?

I'll update my chrome now and see if there's an option somewhere

---

### Post by renkinjutsu on 2010-07-16
updated and aside from a few UI changes, I can't replicate your problem or find an option within chrome that has anything to do with your situation

---

### Post by robsoles on 2010-07-16
> **renkinjutsu said:**
> updated and aside from a few UI changes, I can't replicate your problem or find an option within chrome that has anything to do with your situation

I already played that game dude.

> **cake nom nom said:**
> does not happen in firefox or gedit only chrome ):

OK, let's get on it with it shall we:

Uninstall the one from the repository.

Delete the launcher from your menu and anywhere else you have made one.

Reinstall from the repository.

If you don't have a new launcher then it's a little trickier but easy enough to get around.

If you do have a new launcher then try making the program do the problem again and get back to me what happens please.

---

### Post by cake nom nom on 2010-07-16
> **robsoles said:**
> I already played that game dude.



OK, let's get on it with it shall we:

Uninstall the one from the repository.

Delete the launcher from your menu and anywhere else you have made one.

[http://i29.tinypic.com/2l94opx.png](http://i29.tinypic.com/2l94opx.png)

i completely removed both and my launchers are gone

> **robsoles said:**
> Reinstall from the repository.

If you don't have a new launcher then it's a little trickier but easy enough to get around.

If you do have a new launcher then try making the program do the problem again and get back to me what happens please.

 not sure what to do here

---

### Post by cake nom nom on 2010-07-16
> **renkinjutsu said:**
> updated and aside from a few UI changes, I can't replicate your problem or find an option within chrome that has anything to do with your situation


weird huh. mad annoying i was using the version i downloaded from the google chrome website not ubuntu software center if that helps

---

### Post by cake nom nom on 2010-07-16
> **robsoles said:**
> Yep, I spose that isn't really all that clear as to whether or not it happens in other programs.

Will you please do the test this guy suggested so we can get on with fixing this:

i tried the gedit [www.facebook.com](www.facebook.com) 

i did ctrl+a it did nothing 

i did it several times opening it different times typing in different .com links then highlighting 

it does not happen in firefox, or pidgin or empathy or opera just google chrome. both versions of google chrome the one i got from the software center( the blue circle one) & the one from the website ( the yellow red & green circle icon) when i do ctrl+a on the adress bar.

---

### Post by robsoles on 2010-07-16
<snip> - finally looked at .png picture of synaptic you made - next post is better advice, I promise.

---

### Post by robsoles on 2010-07-16
Sorry, trying to review whole thing and took a look at your picture of synaptic - shows me just the package names to attack!

In terminal issue following:
```
sudo apt-get purge google-chrome-stable
```

When that completes use
```
sudo apt-get purge chromium-browser
```

Now re-install the version that Canonical think is OK.
```
sudo apt-get -f install chromium-browser
```

If launcher is made anew then try it and post back what happens when you test it. If launcher isn't made We help you get that!

---

### Post by cake nom nom on 2010-07-16
well i did the code in the terminal 

drnomnomcake@drnomnomcake-laptop:~$ sudo apt-get -f install chromium-browser
[sudo] password for drnomnomcake: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-browser-inspector chromium-codecs-ffmpeg
Suggested packages:
  chromium-browser-l10n
The following NEW packages will be installed:
  chromium-browser chromium-browser-inspector chromium-codecs-ffmpeg
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/12.7MB of archives.
After this operation, 44.3MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package chromium-browser-inspector.
(Reading database ... 185622 files and directories currently installed.)
Unpacking chromium-browser-inspector (from .../chromium-browser-inspector_5.0.375.99~r51029-0ubuntu0.10.04.1_all.deb) ...
Selecting previously deselected package chromium-codecs-ffmpeg.
Unpacking chromium-codecs-ffmpeg (from .../chromium-codecs-ffmpeg_0.5+svn20100406r43776+43984+43918-0ubuntu1_i386.deb) ...
Selecting previously deselected package chromium-browser.
Unpacking chromium-browser (from .../chromium-browser_5.0.375.99~r51029-0ubuntu0.10.04.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up chromium-browser-inspector (5.0.375.99~r51029-0ubuntu0.10.04.1) ...
Setting up chromium-codecs-ffmpeg (0.5+svn20100406r43776+43984+43918-0ubuntu1) ...
Setting up chromium-browser (5.0.375.99~r51029-0ubuntu0.10.04.1) ...
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/x-www-browser (x-www-browser) in auto mode.
update-alternatives: using /usr/bin/chromium-browser to provide /usr/bin/gnome-www-browser (gnome-www-browser) in auto mode.


--

and before hand i right click application menu deleted both google chrome launchers from the menu now nothing appears lol in the menu

idk how to run it now whats the command?

---

### Post by robsoles on 2010-07-17
in terminal try
```
chromium-browser %U &
```

and tell me result please - if browser opens then try that 'ctrl+a' test again and tell me that result please. (If browser opens we make menu item easy, if not I got another command for you to try)

(I been travelling home or I would have responded sooner!)

---

### Post by cake nom nom on 2010-07-17
agh the pop up is still there


: edit but so are my bookmarks?

---

### Post by robsoles on 2010-07-17
So, bookmarks persisted and so did problem - grr (like you said in your title!)

Let's just quickly make you a launcher in the menu.

(1) Right-click on 'Applications' menu in panel
(2) choose 'edit menus'
(3) click on 'Internet' in left hand side of window that opens
(4) click '+ New Item' on right hand near top
(5) Enter "Chrome" (or whatever you like calling the browser) into '_N_ame:' box
(6) Enter "chromium-browser %U" into 'Comm_a_nd' box
(7) put a comment in if you like.
(8 ) click 'Ok' in little window, click 'Close' in big window
(9) check menuitem opens browser nicely - report failure back to me.

Once that's fixed up, open a terminal window and please get me the output from command:
```
ls -al
```copied and pasted into here again.

---

### Post by lordskid on 2010-07-17
I don't use chromium browser but try to check if there is a .chromium-browser or relatively similar name in your home directory

if so try to rename that folder. see if the problem persists.

edit: the folder is in ~/.config/chromium
use this command
```

mv ~/.config/chromium ~/.config/chromium.bak

```

then run chromium-browser again

---

### Post by robsoles on 2010-07-17
> **lordskid said:**
> I don't use chromium browser but try to check if there is a .chromium-browser or relatively similar name in your home directory

i so try to rename that folder. see if the problem persists.

I have used it and the main place it keeps it's stuff is ~/.config/chromium but it is clear that it is keeping something in a different location either as well or instead - that is why I have asked the OP to post what he gets for listing his whole home folder, if I can't spot it in that the next thing I'll be after is a listing of ~/.config (because I already had OP kill ~/.config/chromium for me once) and then I'll be after listings of suss looking folders in the rest of his home dir.

Is there a .chromium-browser entry in the output I have asked you for cake nom nom?

(Just in case you miss them, instructions for re-making your launcher in post #[**44**]("http://ubuntuforums.org/showpost.php?p=9599733&postcount=44"))

---

### Post by lordskid on 2010-07-17
did you try to rename the .cache/chromium too? (WARNING! don't post it anywhere may store passwords.)
I can only see this two folders coz I read in this thread that guest don't have the mystery behavior.

---

### Post by cake nom nom on 2010-07-17
drnomnomcake@drnomnomcake-laptop:~$ ls -al
total 3420
drwxr-xr-x 66 drnomnomcake drnomnomcake    4096 2010-07-17 03:37 .
drwxr-xr-x  4 root         root            4096 2010-06-17 17:46 ..
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 00:31 .adobe
-rw-------  1 drnomnomcake drnomnomcake    7143 2010-07-17 01:09 .bash_history
-rw-r--r--  1 drnomnomcake drnomnomcake     220 2010-05-26 00:15 .bash_logout
-rw-r--r--  1 drnomnomcake drnomnomcake    3103 2010-05-26 00:15 .bashrc
drwx------ 18 drnomnomcake drnomnomcake    4096 2010-07-17 03:37 .cache
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 11:01 .compiz
drwxr-xr-x 29 drnomnomcake drnomnomcake    4096 2010-07-15 22:46 .config
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-06-21 20:43 Conky
-rw-r--r--  1 drnomnomcake drnomnomcake  177274 2010-06-13 22:52 conkyfonts.zip
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 00:21 .dbus
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-07-17 00:03 Desktop
-rw-r--r--  1 drnomnomcake drnomnomcake      55 2010-07-17 03:37 .dmrc
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-07-17 00:01 Documents
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-07-13 17:14 Downloads
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-07-17 03:38 .dropbox
drwxr-xr-x  5 drnomnomcake drnomnomcake    4096 2010-06-28 01:09 Dropbox
drwxr-xr-x  4 drnomnomcake drnomnomcake    4096 2010-06-20 08:54 .dropbox-dist
drwxr-xr-x  4 drnomnomcake drnomnomcake    4096 2010-07-10 01:45 .emerald
-rw-------  1 drnomnomcake drnomnomcake      16 2010-05-26 00:21 .esd_auth
drwxr-xr-x  8 drnomnomcake drnomnomcake    4096 2010-06-17 17:20 .evolution
-rw-r--r--  1 drnomnomcake drnomnomcake     179 2010-05-26 00:15 examples.desktop
-rw-r--r--  1 drnomnomcake drnomnomcake 1708431 2010-06-11 21:24 Firefox_wallpaper.png
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-07-04 15:34 .fontconfig
drwxr-xr-x  5 drnomnomcake drnomnomcake    4096 2010-06-14 23:16 .fonts
drwx------  2 drnomnomcake drnomnomcake    4096 2010-05-28 01:53 .g2ipmsg
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-07-10 23:09 .gazpacho
drwx------  5 drnomnomcake drnomnomcake    4096 2010-07-17 03:37 .gconf
drwx------  2 drnomnomcake drnomnomcake    4096 2010-07-17 03:39 .gconfd
drwx------  6 drnomnomcake drnomnomcake    4096 2010-05-28 12:11 .gdesklets
-rw-r-----  1 drnomnomcake drnomnomcake       0 2010-07-16 21:58 .gksu.lock
drwx------ 10 drnomnomcake drnomnomcake    4096 2010-07-15 20:46 .gnome2
drwx------  2 drnomnomcake drnomnomcake    4096 2010-05-26 00:22 .gnome2_private
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-28 02:11 .gnome-color-chooser
drwx------  2 drnomnomcake drnomnomcake    4096 2010-06-16 21:41 .gnupg
-rw-r--r--  1 drnomnomcake drnomnomcake      96 2010-06-16 21:35 .gorillarc
drwx------  2 drnomnomcake drnomnomcake    4096 2010-05-28 02:07 .gpass
-rw-r--r--  1 drnomnomcake drnomnomcake     331 2010-06-17 17:10 .gshutdown
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-07-16 22:09 .gstreamer-0.10
-rw-r--r--  1 drnomnomcake drnomnomcake     180 2010-07-17 03:37 .gtk-bookmarks
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-07-12 18:34 .gtkpod
-rw-r--r--  1 drnomnomcake drnomnomcake      41 2010-05-28 02:11 .gtkrc-2.0
-rw-r--r--  1 drnomnomcake drnomnomcake      99 2010-05-28 02:12 .gtkrc-2.0-gnome-color-chooser
dr-x------  2 drnomnomcake drnomnomcake       0 2010-07-17 03:37 .gvfs
-rwxr-xr-x  1 drnomnomcake drnomnomcake      56 2007-11-30 17:50 hddmonit.sh
-rw-------  1 drnomnomcake drnomnomcake   59208 2010-07-17 03:37 .ICEauthority
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-07-16 16:29 .icedteaplugin
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-05-28 11:17 .icons
-rw-------  1 drnomnomcake drnomnomcake       0 2010-05-28 01:53 ipmsg.log
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-27 01:40 .kde
-rw-r--r--  1 drnomnomcake drnomnomcake    2694 2010-06-30 00:40 .keysafe
-rw-r--r--  1 drnomnomcake drnomnomcake  839680 2010-06-13 22:38 lm_sensors-3.1.2.tar (2)
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 00:24 .local
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 00:31 .macromedia
drwx------  3 drnomnomcake drnomnomcake    4096 2010-05-26 09:25 .mission-control
drwx------  4 drnomnomcake drnomnomcake    4096 2010-05-26 00:24 .mozilla
drwxr-xr-x  5 drnomnomcake drnomnomcake    4096 2010-07-11 20:58 Music
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-05-26 00:21 .nautilus
-rw-r--r--  1 drnomnomcake drnomnomcake   81932 2010-06-20 08:49 nautilus-dropbox_0.6.2_i386.deb
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-06-29 23:23 .netx
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-06-13 23:09 .openoffice.org
drwx------ 16 drnomnomcake drnomnomcake    4096 2010-07-10 02:09 .opera
-rw-r--r--  1 drnomnomcake drnomnomcake    3072 2010-05-26 00:22 photos-20100526-0.db
drwxr-xr-x 14 drnomnomcake drnomnomcake    4096 2010-07-14 21:46 Pictures
drwx------  3 drnomnomcake drnomnomcake    4096 2010-06-13 09:19 .pki
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-06-18 23:31 Podcasts
-rw-r--r--  1 drnomnomcake drnomnomcake     675 2010-05-26 00:15 .profile
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-05-26 00:21 Public
drwx------  2 drnomnomcake drnomnomcake    4096 2010-07-17 03:37 .pulse
-rw-------  1 drnomnomcake drnomnomcake     256 2010-05-26 00:21 .pulse-cookie
drwx------  6 drnomnomcake drnomnomcake    4096 2010-07-14 21:46 .purple
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-06-26 00:23 .qt
-rw-------  1 drnomnomcake drnomnomcake   56876 2010-07-17 01:09 .recently-used.xbel
-rw-r--r--  1 drnomnomcake drnomnomcake   31994 2010-06-14 18:24 .recently-used.xbel.0J9LEV
-rw-r--r--  1 drnomnomcake drnomnomcake   31994 2010-06-14 18:17 .recently-used.xbel.4H51DV
drwxr-xr-x  4 drnomnomcake drnomnomcake    4096 2010-07-10 00:43 .screenlets
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-06-13 23:00 scripts
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-05-29 21:45 .SimDock
drwx------  4 drnomnomcake drnomnomcake    4096 2010-07-11 22:18 .Skype
-rwxr-xr-x  1 drnomnomcake drnomnomcake     253 2010-06-16 23:40 .ssc.sh
drwx------  2 drnomnomcake drnomnomcake    4096 2010-05-28 02:08 .ssh
-rw-r--r--  1 drnomnomcake drnomnomcake       0 2010-05-26 00:28 .sudo_as_admin_successful
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-05-26 00:21 Templates
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-05-26 00:38 .themes
drwxr-xr-x  5 drnomnomcake drnomnomcake    4096 2010-05-28 12:11 .thumbnails
drwxrwxr-x  2 drnomnomcake drnomnomcake    4096 2010-06-13 17:41 Ubuntu One
drwxr-xr-x  4 drnomnomcake drnomnomcake    4096 2010-07-10 23:21 .ubuntu-tweak
drwx------  2 drnomnomcake drnomnomcake    4096 2010-06-20 09:19 .update-notifier
drwxr-xr-x  3 drnomnomcake drnomnomcake    4096 2010-07-01 23:02 Videos
drwx------  2 drnomnomcake drnomnomcake    4096 2010-06-13 23:46 .w3m
-rw-r--r--  1 drnomnomcake drnomnomcake     230 2010-06-13 23:46 weather
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-06-18 13:47 Webcam
drwxr-xr-x  4 drnomnomcake drnomnomcake    4096 2010-07-04 15:42 .wine
drwxr-xr-x  2 drnomnomcake drnomnomcake    4096 2010-06-24 01:46 .wireshark
-rw-r--r--  1 drnomnomcake drnomnomcake     559 2010-06-06 15:21 .xscreensaver-getimage.cache
-rw-------  1 drnomnomcake drnomnomcake    5082 2010-07-17 03:41 .xsession-errors
-rw-------  1 drnomnomcake drnomnomcake  135010 2010-07-17 01:09 .xsession-errors.old
drnomnomcake@drnomnomcake-laptop:~$

---

### Post by robsoles on 2010-07-17
OK, Nothing obvious there.

Using '[CTRL]+[H]' make invisible files in your home folder visible in GUI file browser again. Find and delete or rename ~/.config/chromium but definitely delete ~/.cache/chromium ( ~/ represents your own home directory in BASH/terminal )

Re-check the browser for your problem, probably still there and checking re-creates the folders you just got rid of - get rid of them again if problem is still there and give me output to following:
```
ls .config/ -al
```It really should be hiding in there and not in your .cache directory but lets not leave any stone unturned now.

---

### Post by cake nom nom on 2010-07-17
ok i deleted both the folders you told me .cache/chrom & .config/chrome

then reopened the browser and this came up

[http://i30.tinypic.com/5n643k.png](http://i30.tinypic.com/5n643k.png)

i didnt do any option

the problem still there

the folders are back
outcome in terminal


drnomnomcake@drnomnomcake-laptop:~$ ls .config/ -al
total 136
drwxr-xr-x 29 drnomnomcake drnomnomcake 4096 2010-07-17 03:56 .
drwxr-xr-x 66 drnomnomcake drnomnomcake 4096 2010-07-17 03:54 ..
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-10 22:17 autostart
drwxr-xr-x  5 drnomnomcake drnomnomcake 4096 2010-05-28 11:17 awn
drwxr-xr-x  3 drnomnomcake drnomnomcake 4096 2010-07-16 16:41 banshee-1
drwx------  2 drnomnomcake drnomnomcake 4096 2010-07-15 17:51 brasero
drwxr-xr-x  9 drnomnomcake drnomnomcake 4096 2010-07-17 03:37 cairo-dock
drwx------  3 drnomnomcake drnomnomcake 4096 2010-07-17 03:56 chromium
drwx------  3 drnomnomcake drnomnomcake 4096 2010-05-28 02:41 compiz
drwx------  2 drnomnomcake drnomnomcake 4096 2010-05-28 02:43 desktop-couch
drwxr-xr-x  8 drnomnomcake drnomnomcake 4096 2010-07-11 21:46 emesene1.0
drwx------  2 drnomnomcake drnomnomcake 4096 2010-07-17 03:55 Empathy
drwx------  2 drnomnomcake drnomnomcake 4096 2010-05-26 09:28 enchant
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-12 18:33 exaile
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-05-26 00:22 f-spot
drwxr-xr-x  3 drnomnomcake drnomnomcake 4096 2010-05-26 00:22 gnome-disk-utility
drwxr-xr-x  3 drnomnomcake drnomnomcake 4096 2010-06-12 23:09 gnome-session
drwx------  3 drnomnomcake drnomnomcake 4096 2010-07-16 18:51 google-chrome
drwx------  2 drnomnomcake drnomnomcake 4096 2010-07-17 03:54 gtk-2.0
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-06-13 15:50 indicators
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-17 03:41 menus
-rw-r--r--  1 drnomnomcake drnomnomcake  597 2010-05-28 02:16 monitors.xml
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-07-11 22:19 qutim
drwxr-xr-x 40 drnomnomcake drnomnomcake 4096 2010-07-10 00:43 Screenlets
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-06-12 23:09 session-state
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-16 23:09 softwarecenter
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-06-12 18:33 tomboy
drwx------  2 drnomnomcake drnomnomcake 4096 2010-07-12 18:43 totem
-rw-r--r--  1 drnomnomcake drnomnomcake 5807 2010-07-11 20:54 Trolltech.conf
drwx------  2 drnomnomcake drnomnomcake 4096 2010-07-11 00:24 ubuntuone
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-07-11 01:20 ubuntu-tweak
-rw-------  1 drnomnomcake drnomnomcake  626 2010-06-03 01:49 user-dirs.dirs
-rw-r--r--  1 drnomnomcake drnomnomcake    5 2010-05-26 00:21 user-dirs.locale
drnomnomcake@drnomnomcake-laptop:~$

---

### Post by cake nom nom on 2010-07-17
going to have to go back to the drawing board man i just got it in firefox somehow? im uploading a video now

when i was tring to upload the screen shot of when i reopened google chrome after deleting .catch/chrome & .congfig/chrome 

i was on modzilla trying to copy the html to post on here & i  got it it took me for ever to replicate it on video but i did it

---

### Post by cake nom nom on 2010-07-17
thats in modzilla sorry about the annoying infomercial

[http://www.youtube.com/watch?v=iZNijrjtOEs](http://www.youtube.com/watch?v=iZNijrjtOEs)

it happened again when i was trying to copy the link on youtube to post it on here :| it just doesnt happen in the adress bar

---

### Post by robsoles on 2010-07-17
may I have the output to the following please:

```
ls ~/.ubuntu-tweak -al

ls ~/.config/ubuntu-tweak -al
```

Also, please have a very close look through options in compiz-config-settings-manager (install it if it isn't already on your machine) regarding mouse behaviors and assistants to see if any seem relevant to this problem.

I am (also) going to try some creative expressions in Google search to see if I can get a better clue what is happening to/for you!

---

### Post by cake nom nom on 2010-07-17
drnomnomcake@drnomnomcake-laptop:~$ ls ~/.ubuntu-tweak -al
total 16
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-07-10 23:21 .
drwxr-xr-x 66 drnomnomcake drnomnomcake 4096 2010-07-17 04:01 ..
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-10 23:21 scripts
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-10 23:21 templates
drnomnomcake@drnomnomcake-laptop:~$ ls ~/.config/ubuntu-tweak -al
total 28
drwxr-xr-x  4 drnomnomcake drnomnomcake 4096 2010-07-11 01:20 .
drwxr-xr-x 29 drnomnomcake drnomnomcake 4096 2010-07-17 03:56 ..
drwxr-xr-x  3 drnomnomcake drnomnomcake 4096 2010-07-05 01:33 appcenter
-rw-r--r--  1 drnomnomcake drnomnomcake 6025 2010-07-11 01:17 appstatus.json
-rw-r--r--  1 drnomnomcake drnomnomcake   25 2010-07-11 01:20 sourcestatus.json
drwxr-xr-x  2 drnomnomcake drnomnomcake 4096 2010-07-11 01:02 temp
-rw-r--r--  1 drnomnomcake drnomnomcake    0 2010-07-11 01:02 ubuntu-tweak.log
drnomnomcake@drnomnomcake-laptop:~$

---

### Post by cake nom nom on 2010-07-17
> **robsoles said:**
> I am (also) going to try some creative expressions in Google search to see if I can get a better clue what is happening to/for you!


thank you! !

---

### Post by robsoles on 2010-07-17
I haven't managed a clever enough search in Google yet.

Please preview ~/.config/ubuntu-tweak/ubuntu-tweak.log for anything you'd prefer not to share with the world and, if you find nothing of the sort, then attach it to your next post - if it is too personal then consider pm'ing it to me coz I won't show anyone if you send it to me like that.

May I have output from ```
ls ~/.ubuntu-tweaks/scripts
```probably pointless to pursue but the name of one or more of them may make me want to see their contents.

(to preview that log you should be able to navigate to it in GUI file-manager, double-click it and choose 'display...' option)

---

### Post by cake nom nom on 2010-07-17
drnomnomcake@drnomnomcake-laptop:~$ ls ~/.ubuntu-tweaks/scripts
ls: cannot access /home/drnomnomcake/.ubuntu-tweaks/scripts: No such file or directory
drnomnomcake@drnomnomcake-laptop:~$ sudo drnomnomcake@drnomnomcake-laptop:~$ ls ~/.ubuntu-tweaks/scripts
[sudo] password for drnomnomcake: 
sudo: drnomnomcake@drnomnomcake-laptop:~$: command not found
drnomnomcake@drnomnomcake-laptop:~$ sudo ls ~/.ubuntu-tweaks/scripts
ls: cannot access /home/drnomnomcake/.ubuntu-tweaks/scripts: No such file or directory
drnomnomcake@drnomnomcake-laptop:~$ ls ~/.ubuntu-tweaks/scripts
ls: cannot access /home/drnomnomcake/.ubuntu-tweaks/scripts: No such file or directory
drnomnomcake@drnomnomcake-laptop:~$ 




i went to in manually to  double click and "display" it but it's empty or blank( it opens with gedit when i double click)

---

### Post by robsoles on 2010-07-17
I wonder if you could stand making a new account for yourself on your laptop there and migrating all the stuff you can't stand losing from this account to the new one?

Mostly we'd just have to move files from your primary folders (Desktop, Documents, Videos, etc etc) and dodge all the hidden folders (problem is hiding in one of those and seems too hard to find like this :() and we'd have to make sure your new user was a member of important admin groups like wheel and a couple of others.

Is this a tenable solution to you? (If it is don't race into it and **definitely** don't remove your current account till completely satisfied new account has all desirable stuff from it!)

I will be offline for a couple of hours from about 30 minutes time.

---

### Post by cake nom nom on 2010-07-17
I suppose i could do that ill get back to you later on today see how it went

---

### Post by cake nom nom on 2010-07-17
i think ill just do a fresh install

---

### Post by robsoles on 2010-07-17
(Good Morning, 6.20am as I type here - how about there?)

Have you reinstalled? If not, I will post the cleanest way I know of to give a new account all the personal files and best bits of your old account.

EDIT: Family obligations are going to drag me offline about 9.30am my time (EST) and keep me off for an unknown period so I'll add a couple of comments I hope will help.

Reinstalling the whole OS but keeping your home directory is likely to give you back the problems you had as soon as you install the programs you had the problems with - there is a slim chance that the problems don't re-occur but the fact that you could log on as a guest user and not experience the problem makes that less likely.

Just copying or moving the folders and files that aren't hidden from your home directory into a new user's home directory is a way you could have the basic stuff you own in an account that shouldn't be suffering the problem(s) without reinstalling - programs like virtualbox use a hidden directory to keep **your** stuff in but it's easily identified and copying or moving it's contents to the new account retains that stuff.

I will be back online in a few hours and quite happy to guide you through copying or moving your stuff to a new user account if you want to pursue the option and are at all worried about dropping any of your stuff.

---

### Post by cake nom nom on 2010-07-18
dang already reformatted lol where should i install google chrome from?

---

### Post by robsoles on 2010-07-18
Get it from Canonical repository and try out what they think is good stuff.

---

### Post by cake nom nom on 2010-07-18
> **robsoles said:**
> Get it from Canonical repository and try out what they think is good stuff.

?

---

### Post by robsoles on 2010-07-18
Open software center.

Type 'chromium' into search box.

if 'chromium-browser' doesn't appear in list then use 'edit'->'software sources' to enable 'other software' and stuff till you can get it in your list (by memory, it is in the initial list in a new install but just in case...)

Click 'Install' button, wait, viola - from the Canonical repository and shouldn't exhibit that problem you were having without at least some tinkering on your part!

---

### Post by cake nom nom on 2010-07-19
okay yeah it doesn't have the problem I appreciate all of the help everyone provided especially robsoles thanks again

---

### Post by Digitart on 2010-10-10
> **cake nom nom said:**
> how do i get rid of this little box everytime i try to hit ctrl+a to highlight the whole search bar to type somthing in or double click to highlight 

a little popup box comes up asking me if i want to open with fire fox or send url or open with opera or modzilla its mad annoying i cant find anywhere how to get rid of it can anyone help? heres a video i took to show what it is

[http://www.youtube.com/watch?v=4LMyWfIqup0](http://www.youtube.com/watch?v=4LMyWfIqup0)
Absolute anoying problem. I finaly found a better solution in this very forum that doesn't require to reinstall nothing: [http://ubuntuforums.org/showthread.php?p=8814042](http://ubuntuforums.org/showthread.php?p=8814042) and [http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2010-06/msg01828.html](http://linux.derkeiler.com/Mailing-Lists/Ubuntu/2010-06/msg01828.html)

This is a "feature" of Cairo Dock's plugin "Clipper".
Simply disable it or go to Clipper configuration and uncheck "enable actions".

Now in spanish:
Cada vez que seleccionaba Ctrl+A (seleccionar todo) en una dirección url en Chrome salía un estorboso popup con los letreros "Abrir en Firefox", "Enviar URL", "Abrir con Mozilla" y "Abrir con Opera" que se instalaba por 4 segundos y no dejaba escribir en la barra de direcciones.
Este es un ejemplo del problema:
[http://www.youtube.com/watch?v=4LMyWfIqup0](http://www.youtube.com/watch?v=4LMyWfIqup0)

El causante es el plugin llamado "Clipper" (Historial del portapapeles) de Cairo Dock.
Para solucionarlo basta con entrar a la configuración de Cairo Dock en la sección de "Accesorios" y desactivar "Historial del portapapeles".
Si el plugin te gusta y quieres dejarlo activado, da click con el botón derecho sobre Clipper y elige "Configurar esta mini-aplicación"->Configuración y desactiva "¿Activar acciones?"

---

