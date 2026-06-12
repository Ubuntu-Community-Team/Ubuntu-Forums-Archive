---
title: "Thunderbird won't open links"
date: 2006-04-26
forum: General Help
---

### Post by The Pinny Parlour on 2006-04-26
Hi all,

I have tried to scour the 'Search' feature on this forum for answers, but come up with solutions that don't work for me, or I don't know how to implement them.

Basically, thunderbird won't open links. 

The Thunderbird was installed using Automatix.  I use Swiftfox as browser.

Any help would be great,

Regards,
Ian

---

### Post by jazzmuzik on 2006-04-26
I think you need to do this: go into System, Preferences, Preferred Applications and see what the setting is for Web Browser. Set that to Custom and point it at Swiftfox.

---

### Post by The Pinny Parlour on 2006-04-26
Hi,

Yes thanks,  tried that. It already is pointing to Swiftfox - usr/home/swiftfox %s

Regards,
Ian

---

### Post by The Pinny Parlour on 2006-04-26
Hi,

I get this messege from time to time when trying to open links from within Thunderbird:  "Galeon Failed To Start. The existing Galeon instance is not responding. Terminating the "galeon" processes may fix the problem."


I also changed my preferred custom browser to:

/home/*/swiftfox/firefox %s

Still no luck

Regards,
Ian

---

### Post by jazzmuzik on 2006-04-26
usr/home/swiftfox %s

is wrong. First of all, are you trying to point to the /usr directory, or do you have a usr directory branching off of /home/youraccount ? In either case the above won't work for either.

There is no /usr/home directory. There's a /usr directory and there's a /home directory. Find where the swiftfox file resides and put that into the preferred applications.

Try this:

whereis swiftfox

---

### Post by The Pinny Parlour on 2006-04-26
I have a shortcut to Swiftfox on the desktop and I just copy the shortcut directory on that:  /home/myname/swiftfox/firefox

Unfortunatly, it still doesn't work.  argh  Surely it can't be that hard to make a link in Thunderbird email open a web browser?

Thank you for trying.


Regards,
Ian

---

### Post by The Pinny Parlour on 2006-04-26
This is turning very bad very quickly.  I also have discovered that mailto: links in SwiftFox won't open Thunderbird.  What is going on here?  This is strange.  I don't want to go back to windows for my emails.

Regards,
Ian

---

### Post by jazzmuzik on 2006-04-26
Open a terminal and run this:

/home/myname/swiftfox/firefox

Does it load firefox?

What does it show when you run:

ls -l /home/myname/swiftfox/firefox

---

### Post by The Pinny Parlour on 2006-04-26
Update:  Have managed to get mailto:   to work in FireFox (Swiftfox)

by opening about:config   and right clicking on a blank area and select new string....then I add   network.protocol-handler.app.mailto   then    /usr/bin/mozilla-thunderbird



That solves mailto: links       Now if I could get ThunderBird to open links embedded in emails.

---

### Post by Efwis on 2006-04-26
[QUOTE=The Pinny Parlour]Update:  Have managed to get mailto:   to work in FireFox (Swiftfox)

by opening about:config   and right clicking on a blank area and select new string....then I add   network.protocol-handler.app.mailto   then    /usr/bin/mozilla-thunderbird



That solves mailto: links       Now if I could get ThunderBird to open links embedded in emails.[/QUOTE]
did you check the settings in Thunderbird to make sure it is pointing to the correct browser?

I run evolution on my breezy install so I don't have it available to check the exact location under edit>preferences.

---

### Post by The Pinny Parlour on 2006-04-26
[QUOTE=jazzmuzik]Open a terminal and run this:

/home/myname/swiftfox/firefox

Does it load firefox?
[/QUOTE]

Yes it does

---

### Post by The Pinny Parlour on 2006-04-26
[QUOTE=Efwis]did you check the settings in Thunderbird to make sure it is pointing to the correct browser?
[/QUOTE]

Not really sure where to check this, but I did go through it anyway and I couldn't find anything obvious like changing default browsers or similar.

---

### Post by The Pinny Parlour on 2006-04-26
I'm sure there is just a setting that needs to be altered or added to Thunderbirds config file that is much similar to firefox's, about:config, that will fix this issue.  I just haven't worked it out yet.

Than you so far those who have helped.

Regards,
Ian

---

### Post by aysiu on 2006-04-26
[QUOTE=The Pinny Parlour]I'm sure there is just a setting that needs to be altered or added to Thunderbirds config file that is much similar to firefox's, about:config, that will fix this issue.  I just haven't worked it out yet.[/QUOTE] Read [this thread](http://www.ubuntuforums.org/showthread.php?t=60427).

---

### Post by jazzmuzik on 2006-04-26
I don't think you select the browser through Thunderbird's settings. I'm pretty sure it's through System, Preferences, Preferred Applications.

---

### Post by Efwis on 2006-04-26
[QUOTE=jazzmuzik]I don't think you select the browser through Thunderbird's settings. I'm pretty sure it's through System, Preferences, Preferred Applications.[/QUOTE]
unfotunately that doesn't always work.

---

### Post by jazzmuzik on 2006-04-26
> /home/myname/swiftfox/firefox

Does it load firefox?

Yes it does

Then put "/home/myname/swiftfox/firefox %s" into System, Preferences, Preferred Applications, Custom, Command.

---

### Post by jazzmuzik on 2006-04-26
[QUOTE=Efwis]unfotunately that doesn't always work.[/QUOTE]

I'm noticing something screwy on my system with System, Preferences, Preferred Applications. Something is broken. I get values, then they disappear, then I try and type in one character but then when I enter a second one the first one disappears. There's a bug there.

There is a gnome tool to change various properties which might provide a clue. Let me see if I can find it.

---

### Post by jazzmuzik on 2006-04-26
Now things seem to be working and I didn't even do anything.

Anyway, I'll try again.

I've created a Firefox launch script called fx1. It launches urls whether Firefox is loaded or not, and puts new urls into a new tab. If you want to try it: Give the script execute properties (chmod 755 fx1) and put it in /home/user/bin . Here's the script (fx1):

```

#!/bin/bash
# This script runs Firefox
browserPath="/usr/bin/firefox"

url="$@"
$browserPath -remote "ping()"
# $? = false if running, true if not
if [ $? = 0 ] ; then
        exec $browserPath -remote openURL"($url,new-tab)"
else
        $browserPath $url &
fi
exit

```

Set "browserPath" to the actual location of the Firefox (or SwiftFox) executable. It could be at /usr/bin/firefox, the default, or somewhere in your home directory.

Now, go into System, Preferences, Preferred Applications, Web Browser, Custom and enter the following:

```
/home/user/bin/fx1 "%s"
```

where user is your user account name.

Now go into Thunderbird and click on a URL in one of your emails and see if it launches Firefox. It does for me.

---

### Post by eiffel on 2006-04-26
> **jazzmuzik]
```

#!/bin/bash
# This script runs Firefox
browserPath="/usr/bin/firefox"

url="$@"
$browserPath -remote "ping()"
# $? = false if running, true if not
if [ $? = 0 ]  said:**
> 

Tried that but get [QUOTE]Error: Failed to send command: 500 command not parseable

Any ideas?

---

### Post by jazzmuzik on 2006-04-26
My apologies for those following along. I had to make some corrections to the instructions above. It seems to be correct now. Try again if you didn't succeed at first.

---

### Post by jazzmuzik on 2006-04-26
[QUOTE=eiffel]Tried that but get 

Any ideas?[/QUOTE]

That's a normal response if you have Firefox already loaded. Try it with Firefox closed. You see, the script checks to see if Firefox is already loaded or not, so it will print an error message one way or the other, just ignore it, but the script takes those return values and either launches Firefox if it's not loaded at all, or it puts the url into a new tab if it is already loaded. See? Pretty cool once you get it working.

---

### Post by eiffel on 2006-04-26
> **jazzmuzik]#!/bin/bash
# This script runs Firefox
browserPath="/usr/bin/firefox"

url="$@"
$browserPath -remote "ping()"
# $? = false if running, true if not
if [ $? = 0 ]  said:**
> 

Am still getting 

[QUOTE]Error: Failed to send command: 500 command not parseable

---

### Post by jazzmuzik on 2006-04-26
Yes. As I explained my script will utilitze this error so you can ignore it. Now specify the fx1 script as your preferred browser. Then test by launching a URL from within Thunderbird. Does it work? It works for me.

---

### Post by The Pinny Parlour on 2006-04-26
[QUOTE=jazzmuzik]Then put "/home/myname/swiftfox/firefox %s" into System, Preferences, Preferred Applications, Custom, Command.[/QUOTE]


Have thought of that and done so already.

Thank You,
Ian

---

### Post by The Pinny Parlour on 2006-04-26
[QUOTE=aysiu]Read [this thread](http://www.ubuntuforums.org/showthread.php?t=60427).[/QUOTE]


Hello aysiu,

I tried to implement this but I have no idea where or how these .js are.  

The following makes no sense to me:

<snip>
edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:
Code:

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox"); user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".

</snip>

If you could tell me where I find these files I could try these.  Of course I would have to edit the firefox directory to match my own.

Regards,
Ian

---

### Post by arnieboy on 2006-04-26
the solution is in the following post:
[http://ubuntuforums.org/showpost.php?p=779915&postcount=393](http://ubuntuforums.org/showpost.php?p=779915&postcount=393)
However this is for opening links in firefox. (u just need to change firefox to swiftfox)
hope this helps.

---

### Post by The Pinny Parlour on 2006-04-27
[QUOTE=arnieboy]the solution is in the following post:
[http://ubuntuforums.org/showpost.php?p=779915&postcount=393](http://ubuntuforums.org/showpost.php?p=779915&postcount=393)
However this is for opening links in firefox. (u just need to change firefox to swiftfox)
hope this helps.[/QUOTE]


Hi arnieboy,

Well done.  You have done it.  I sincerely thank you.  :) 

Regards,
Ian

---

### Post by The Pinny Parlour on 2006-04-27
Just to add, anyone who is trying to implement what arnieboy has posted in their own thunderbird, firstly find the directory path to your browser then type that in where it says:  x-www-browser.  All works.  

It maybe very n00bish to write this but I know there are alot who really don't know yet the things that others find simple.

<snip>

Quote:
Originally Posted by coldrick
3) This *is* a problem: hyperlinks in emails do *not* get sent to Firefox when clicked.
solve this the following way:
in thunderbird:
go to edit --> preferences --> Advanced --> General --> Config editor
and look for the following 2 options:
Quote:
network.protocol-handler.app.https
network.protocol-handler.app.http

double click on each of them and change their values from x-www-browser to firefox
close config editor and preferences.
now all hyperlinks will open in firefox.
</snip>

---

### Post by caos30 on 2007-07-28
Hi, due to the above posts i could resolve this problem successfully. Thanks good people!!!

But i think that all the before can do it more simply for newbies ;)

The steps are very very easy, and this function (ubuntu 7.04, Thunderbird 2.0.0.5):

[INDENT]-Open Thunderbird
- Go to menu: Edit > Preferences > Advanced > General > Config Editor
- Type in the box Filter: network.protocol-handler
- You must see only lines that begin with "network.protocol-handler"
- Check that the next lines are exactly like here:

[COLOR="SeaGreen"] network.protocol-handler.app.file | user set | string | mozilla-firefox
 network.protocol-handler.app.ftp | user set | string | mozilla-firefox
 network.protocol-handler.app.http | user set | string | mozilla-firefox
 network.protocol-handler.app.https | user set | string | mozilla-firefox[/COLOR]

- If some of above lines not exist append it clicking with the right button mouse over any line of the list-box (don't matter wich), and choose: New > String
- If some of above lines exists only check if the "Value" (last parameter) is "mozilla-firefox". If not, modify it (also clicking with the right button mouse).
[/INDENT]

This would be enough. After you have closed all the config windows and have returned to your mails folders, try to do click over any link you have in any mail and it would open the link in a Firefox window. Alert, because if you have opened some firefox window then the link in the mail could be opened in a "new tab" of that firefox window ;)

Before this changes in the thunderbird config editor, you should check that "mozilla-firefox" run effectively the FirefFox navigator in your machine ;) Check this writing "mozilla-firefox" in your Terminal. 

I hope you all could understand-me :D 
Regards from Barcelona!

---

