---
title: "Making Firefox 3.5 Prefered App?"
date: 2009-09-30
forum: General Help
---

### Post by sandman3838 on 2009-09-30
Hello

I just installed Firefox 3.5.3 through Synaptic Package Manager.  It does say Sheretoko?

My issue is this, my Bookmarks work just great within Firefox.  However if I save a Bookmark to my desktop or any other location Firefox 3.0 opens up.  Now I did remove Firefox 3.0 thinking that the bookmarks would switch to Firefox 3.5?  The strange think here is that I get Thunderbird?  Weird!

Oh!  My preferred program for the Web Browser is at Custom with firefox-3.5 %u

Is there a way to make Firefox 3.5 the dominate web browser?

Thank you
Sincerely,

---

### Post by Johnny B on 2009-09-30
you could try making a link to firefox-3.5
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox

---

### Post by DeMus on 2009-09-30
> **sandman3838 said:**
> Hello

I just installed Firefox 3.5.3 through Synaptic Package Manager.  It does say Sheretoko?

My issue is this, my Bookmarks work just great within Firefox.  However if I save a Bookmark to my desktop or any other location Firefox 3.0 opens up.  Now I did remove Firefox 3.0 thinking that the bookmarks would switch to Firefox 3.5?  The strange think here is that I get Thunderbird?  Weird!

Oh!  My preferred program for the Web Browser is at Custom with firefox-3.5 %u

Is there a way to make Firefox 3.5 the dominate web browser?

Thank you
Sincerely,

Do you have a link to FF 3.5 on your desktop? If not, open menu Applications -> Internet and right-click on the FF 3.5 link. Choose to make a copy on the desktop.
Then right-click the link on your desktop and choose properties. Copy the contents of the field command. (Ctrl-c)
Open Menu System -> Preferences -> Preferred Applications.
At Webbrowser choose custom in the dropdown button. In the field command paste your copied command from the desktop link.
From now on FF 3.5 is your preferred browser.

---

### Post by sandman3838 on 2009-10-01
Thanks for the reply!
I did run the line as you suggested.
However it may have made things worse?
Also, I just realized that you may have mis-understood my problem.

Creating an Icon/Shortcut/Link to any Firefox version on the desktop is not a problem.  I usually just go into the Programs Menu and Right Click and select “Add Launcher to Desktop”.  This works and my Homepage Google opens right up.

This might clear it up?
The link to this Issue right now reads:
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8033757](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8033757)

If I drag the address line to the desktop I will get a link that says:
Link to Ubuntu Forums - Reply to Topic

Now if I close Firefox and double click this new link Firefox 3.0 open up not Firefox 3.5.

I'm not sure but now after running 
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox

My Hyperlink association may be messed up?
In the Email I received on this, it read:
**************************************************************
Johnny B has just replied to a thread you have subscribed to entitled - [ubuntu] Making Firefox 3.5 Prefered App? - in the General Help forum of Ubuntu Forums.

This thread is located at:
[http://ubuntuforums.org/showthread.php?t=1279537&goto=newpost](http://ubuntuforums.org/showthread.php?t=1279537&goto=newpost)

Here is the message that has just been posted:
***************
you could try making a link to firefox-3.5
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox
***************


There may also be other replies, but you will not receive any more notifications until you visit the forum again.

All the best,

************************************************************** 
Now when I click on 
[http://ubuntuforums.org/showthread.php?t=1279537&goto=newpost](http://ubuntuforums.org/showthread.php?t=1279537&goto=newpost) 

I get “SERVER NOT FOUND” with a address line of 
[http://www.%u.com/](http://www.%u.com/)

Can I revert the command
sudo ln -s /usr/bin/firefox-3.5 /usr/bin/firefox

Still again thanks for the help.
Any suggestions?

---

### Post by DeMus on 2009-10-01
Yes, something definitely went wrong here. What I wrote was to make a copy of the link in the internet start menu to your desktop.
In the command line of the properties of this link you find something like: 
> /usr/bin/firefox-3.5
Copy this with "ctrl c"

Then you should open the menu System -> Preferences -> Preferred application and under webbrowser choose custom. In the command field paste the command line of your FF 3.5 link, thus:
> /usr/bin/firefox-3.5

I started my answer with the creation of the link on your desktop in case you did not have that.
Just do as I write here and it should work. Really.

---

### Post by sandman3838 on 2009-10-01
Hello
Thanks for the help.

However I did as you suggested and using Custom setting with:
/usr/bin/firefox-3.5 

The Desktop/Folder Web Links to even this issue still open to Firefox 3.0
Oh, I did restart the computer.  Just in case.

Any more suggestions.

Did I install the correct Firefox 3.5?
Perhaps if I removed both 3.0 and 3.5 and then reinstall 3.5 it would do a better job of taking control of the files?

Again thanks for the help.

---

### Post by running_rabbit07 on 2009-10-01
> **DeMus said:**
> Do you have a link to FF 3.5 on your desktop? If not, open menu Applications -> Internet and right-click on the FF 3.5 link. Choose to make a copy on the desktop.
Then right-click the link on your desktop and choose properties. Copy the contents of the field command. (Ctrl-c)
Open Menu System -> Preferences -> Preferred Applications.
At Webbrowser choose custom in the dropdown button. In the field command paste your copied command from the desktop link.
From now on FF 3.5 is your preferred browser.
+1 I actually used this to make all weblinks such as those in Thunderbird open in Epiphany.

---

### Post by running_rabbit07 on 2009-10-02
> **sandman3838 said:**
> Hello
Thanks for the help.

However I did as you suggested and using Custom setting with:
/usr/bin/firefox-3.5 

The Desktop/Folder Web Links to even this issue still open to Firefox 3.0
Oh, I did restart the computer.  Just in case.

Any more suggestions.

Did I install the correct Firefox 3.5?
Perhaps if I removed both 3.0 and 3.5 and then reinstall 3.5 it would do a better job of taking control of the files?

Again thanks for the help.
From the advice above you should be entering this ```
firefox-3.5 %u
``` into the System>Preferences>Preferred Applications You will also have to change the scroller to Custom.

---

### Post by running_rabbit07 on 2009-10-02
> **running_rabbit07 said:**
> From the advice above you should be entering this ```
firefox-3.5 %u
``` into the System>Preferences>Preferred Applications You will also have to change the scroller to Custom.

Did that get it? 

The other poster only wanted you to get the Shiretoko Icon on the desktop so that you could right-click it and get the command out of the properties box to use in the preferences menu.

---

### Post by sandman3838 on 2009-10-02
Thanks for the help.

However firefox-3.5 %u
It was my original listing.
I mentioned it on my first post.

What if I removed both versions of Firefox and ran this:
*************************************************************

How to Download & Install Firefox 3.5 on Ubuntu Linux

Method 1: Installing Via Repository

If you are downloading firefox for first time on your Linux box then add following repository to source list. Others please skip to step 3

1. Open your Terminal and run following command

echo ‘deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’ >> /etc/apt/sources.list

echo ‘deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main’ >> /etc/apt/sources.list

2. Add the Launchpad PPA GPG key:

sudo apt-key adv –keyserver keyserver.ubuntu.com –recv-keys 247510BE

3. Now run below command on your terminal

sudo apt-get update && sudo apt-get install firefox-3.5

---

### Post by sandman3838 on 2010-01-02
I got this Solved with the one of the Ubuntu updates.   This is no longer an issue.

---

