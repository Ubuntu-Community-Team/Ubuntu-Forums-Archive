---
title: "Your preferences can not be read"
date: 2010-06-01
forum: General Help
---

### Post by TheNerdAL on 2010-06-01
When I open Google Chrome, it says "Your preferences can not be read.Some features may be unavailable and changes to preferences won't be saved."

How do I fix this? Thanks.

---

### Post by TeoBigusGeekus on 2010-06-01
Go to
/home/yourusername/.config/chrome/Default/
and delete the preferences file.
Next time you open Chrome it will be regenerated, but you will have to reconfigure Chrome (unfortunately).

---

### Post by TheNerdAL on 2010-06-01
> **TeoBigusGeekus said:**
> Go to
/home/yourusername/.config/chrome/Default/
and delete the preferences file.
Next time you open Chrome it will be regenerated, but you will have to reconfigure Chrome (unfortunately).

Thanks!

---

### Post by TheNerdAL on 2010-06-02
> **TeoBigusGeekus said:**
> Go to
/home/yourusername/.config/chrome/Default/
and delete the preferences file.
Next time you open Chrome it will be regenerated, but you will have to reconfigure Chrome (unfortunately).

It does it still.

---

### Post by TeoBigusGeekus on 2010-06-02
Ok... delete the whole chrome folder.
If it persists, purge chrome and reinstall it.

---

### Post by TheNerdAL on 2010-06-02
> **TeoBigusGeekus said:**
> Ok... delete the whole chrome folder.
If it persists, purge chrome and reinstall it.

I removed Chrome and reinstalled it but still the same problem.

---

### Post by TeoBigusGeekus on 2010-06-03
You also have to remove the chrome folder from .config.
Something must be broken in there.

---

### Post by TheNerdAL on 2010-06-03
> **TeoBigusGeekus said:**
> You also have to remove the chrome folder from .config.
Something must be broken in there.

Thanks! :)

---

### Post by dexlavis on 2010-06-18
As explained here: [http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/](http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/), you might not have to delete files to fix this, because the files

/home/*<user>*/.config/google-chrome/Local State 
/home/*<user>*/.config/google-chrome/Default/Preferences

might have had their owner changed for some reason. (*<user>* being your login name). 

Open a terminal and change it back like so:
```

cd ~
cd .config/google-chrome
sudo chown *<user>*:*<user>* Local\ State
sudo chown *<user>*:*<user>* Default/Preferences
```
Done. Worked for me.

---

### Post by metalf8801 on 2010-06-29
> **dexlavis said:**
> As explained here: [http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/](http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/), you might not have to delete files to fix this, because the files

/home/*<user>*/.config/google-chrome/Local State 
/home/*<user>*/.config/google-chrome/Default/Preferences

might have had their owner changed for some reason. (*<user>* being your login name). 

Open a terminal and change it back like so:
```

cd ~
cd .config/google-chrome
sudo chown *<user>*:*<user>* Local\ State
sudo chown *<user>*:*<user>* Default/Preferences
```
Done. Worked for me.

I'm just trying to make this a little clearer 
I think the \ in Local State is a typo and Local State needs to be in quotes because of the space in the file name 

```

cd ~
cd .config/google-chrome
sudo chown *<your user name>*:*<your user name>* 'Local State'
sudo chown *<your user name>*:*<your user name>* Default/Preferences
```

well thats what worked for me 
Thank you dexlavis for finding the solution

---

### Post by esoniat on 2010-08-15
Just resetting all of the ownership might be simpler and safe.
cd ~/.config
chown -R <user>:<user> google-chrome

This way file names are not a problem and in the future other files effected will be changed.

For me it looks like I had somehow run chrome as a root process but without changing my environment so chrome touched my files as a root process changing the ownership to root.

---

### Post by MartyLab on 2010-11-04
A HUGE Thank you to the contributors to this thread :)

I had also run google-chrome as root ](*,)

In my case I found that a slight variation of the above post was needed as I got...

chown: changing ownership of `./google-chrome/Local State': Operation not permitted
chown: changing ownership of `./google-chrome/Default/Preferences': Operation not permitted

```
myusername@homer-laptop:~$ [COLOR="Red"]cd .config[/COLOR]
myusername@homer-laptop:~/.config$ [COLOR="Red"]sudo chown -cR myusername:myusername .[/COLOR]
[sudo] password for myusername: 
changed ownership of `./google-chrome/Local State' to myusername:myusername
changed ownership of `./google-chrome/Default/Preferences' to myusername:myusername
```

It worked for me :)

I hope that helps somebody else.

---

### Post by rainy pinoko on 2010-12-14
Code:

cd .config
sudo chown -cR username:username .

Worked for me! Thank you! My problem is solved :P

---

### Post by billrandle on 2010-12-19
I had the same problem...this worked for me.

```
cd ~
cd .config/google-chrome
sudo chown <your user name>:<your user name> 'Local State'
sudo chown <your user name>:<your user name> Default/Preferences
```

Thanks
:D

---

### Post by complience on 2011-03-13
Thanks this fixed the problem
but what I want to know what 'CAUSED' the problem to happen in the first place?

any ideas - ive been having lots of problems with google chrome randomly crashing and wonder if this is related?

---

### Post by metalf8801 on 2011-03-14
> **complience said:**
> Thanks this fixed the problem
but what I want to know what 'CAUSED' the problem to happen in the first place?

any ideas - ive been having lots of problems with google chrome randomly crashing and wonder if this is related?

I just ran into this problem again I don't remember what happened last time. However, this time I'm almost positive it happened because I ran Chromium (the open source version of Chrome) as root. I ran Chromium as root because I was doing some trouble shooting the other day and I needed root privileges to get a full bug report from Bug Buddy. I have been having problems with watching flash videos on youtube but not videos using WebM. However, I'm not having any problems playing flash videos on Hulu or Fancast. 

I just tried running Chromium as root again to make sure it was the cause and I got some interesting errors I just wish I knew what they meant. 
```
~/.config$ sudo chromium-browser %U
[8304:8304:23331825319:ERROR:extension_prefs.cc(734)] Bad or missing pref 'state' for extension 'hpibmhghjndideebpackbdlpncgkcppp'
[8304:8304:23331825395:ERROR:extension_prefs.cc(734)] Bad or missing pref 'state' for extension 'lncjcfkpannmofmpgdfoonkniofdnaba'

```
I then opened Chromium and got the "Your preferences can not be read" message again. So for me at least this problem was caused by running Chromium as root.

To fix it I used 
```
~/.config$ sudo chown -cR myusername:myusername chromium 
changed ownership of `chromium/Default/Preferences' to myusername:myusername
changed ownership of `chromium/Default/Last Session' to myusername:myusername
changed ownership of `chromium/Default/Last Tabs' to myusername:myusername
changed ownership of `chromium/Local State' to myusername:myusername

```
What's interesting is that I had not seen the following output when I used the same command a few minuets again. 
```
changed ownership of `chromium/Default/Last Session' to myusername:myusername
changed ownership of `chromium/Default/Last Tabs' to myusername:myusername

```
 
This should confirm 
> **esoniat said:**
> 
For me it looks like I had somehow run chrome as a root process but without changing my environment so chrome touched my files as a root process changing the ownership to root.

---

### Post by coleki on 2011-03-16
I had a very similar problem. I got the same error pop-up, but twice in a row. In my case, for some reason, trying the chown solution didn't work, but purging google-chrome (and replacing it with google-chrome-stable) did. I also did do an:

rm -R -f /home/<your user name>/.config/google-chrome

---

### Post by platanofrito on 2011-04-06
The following error shows up when I first start Chromium 10.0.648.133 (77742) under Ubuntu 10.04.

"Your preferences can not be read.

Some features may be unavailable and changes to preferences won't be saved."



Many thanks to metalf8801 and his post above.  This solved my problem, and just in the nick of time.  I was about to jump ship on the Chromium browser altogether, but happened to cross this thread as a last ditch attempt.  I had tried many other posts and used their syntax, but none of them worked for me.  Here is what I used and it worked for me:

cd ~/.config$ 
sudo chown -cR myusername:myusername chromium

*Of course you must substitute <yourusername> above.

Sorry if I'm making this child proof, but you know how it is.

Again, all the credit goes to metalf8801 for this one.  This experience has renewed my faith in the Ubuntu forum and its community of users.  Thanks again.

---

### Post by asn_knight on 2011-04-16
> **dexlavis said:**
> As explained here: [http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/](http://ahmadzz.wordpress.com/2010/05/14/google-chrome-error/), you might not have to delete files to fix this, because the files

/home/*<user>*/.config/google-chrome/Local State 
/home/*<user>*/.config/google-chrome/Default/Preferences

might have had their owner changed for some reason. (*<user>* being your login name). 

Open a terminal and change it back like so:
```

cd ~
cd .config/google-chrome
sudo chown *<user>*:*<user>* Local\ State
sudo chown *<user>*:*<user>* Default/Preferences
```
Done. Worked for me.

Thanks a lot!! Worked for me too!! :) :)

---

### Post by jadonchristensen on 2011-04-26
I am using Chromium from Ubuntu Software Center on Ubuntu 11.04

cd /home/USERNAME/.config
sudo chown -R username:username chromium

Username being the user that I am logged in as.
This worked for me.

---

