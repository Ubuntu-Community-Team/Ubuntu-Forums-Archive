---
title: "Main Menu problem in 11.10"
date: 2011-10-26
forum: General Help
---

### Post by valvegrid on 2011-10-26
This may or may not be a problem, I'm not sure. When I open up the Main Menu I can't seem to add a New Item or New Menu or even look at the properties of existing items. This used to work in all the other versions of Ubuntu, but not this one. I have had a search, but there doesn't seem to be any other posts about it.

I did upgrade from 11.04 and I'm not sure if it was working in that version, should I just reinstall 11.10 instead?

---

### Post by garvinrick4 on 2011-10-26
Try this:
```
sudo apt-get clean
```
```
sudo apt-get install --reinstall alacarte
```See if main menu will now open and work for you. (main menu is "alacarte"

---

### Post by valvegrid on 2011-10-26
> **garvinrick4 said:**
> Try this:
```
sudo apt-get clean
``````
sudo apt-get install --reinstall alacarte
```See if main menu will now open and work for you. (main menu is "alacarte"

I tried that, and still no go. 

I might revert back to 10.04 LTS as that was working faultlessly, there appear to be other issues with 11.10.

Thanks for the help, don't think I'm being rude, I have to get ready for work, so I'll check back in the morning.

---

### Post by garvinrick4 on 2011-10-26
> I might revert back to 10.04 LTS as that was working faultlesslyThat is fine sticking with LTS versions are very, very stable.

> 
I might revert back to 10.04 LTS as that was working faultlessly, there appear to be other issues with 11.10.##It is a small percentage of users that have problems I believe. Some are legit and some are not as per below.
With every new version there is a rush of new users who install and do not quite seem to
install correctly and or have not given any time for learning curve of a new operating system 
for themselves so a lot of problems that are more made be themselves playing
with config files and such. No other operating system they have used has allowed them access to
config files so they seem to make a mess then get in Forum and need assistance, which is fine. They do not
tell you what has happened to get to the situation they are in. Most of time we just try
to help out and not bring up what they have messed with prior to their problem. We more
or less know because we did it or have seen it ourselves many times. (most all of us here have a real passion for Ubuntu linux and would like to see many more have the same)
If new users would read the "show me hows" before installing at:
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 
before installing and read a post installation guide for their version installed[U]
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

Just like a user did when they first picked up a mouse to use Windows.


[/U]

---

### Post by valvegrid on 2011-10-27
Thanks again for that. Because the operating system has been installed from new, I haven't had a chance to mess with config files. All I have done is to install 11.04 first then install 11.10 next. I did back up my /home folder which might have caused a problem because that backs up the config files for the applications that I use, I will try and back up just the files I need and exclude most of the config files I don't need, because I suspect that might be causing a problem as I notice there is a lot of squit that shouldn't be there.

It probably will not be till the weekend now, I have to earn some money. I will feedback sometime over the weekend.

---

### Post by garvinrick4 on 2011-10-27
> Thanks again for that. Because the operating system has been installed  from new, I haven't had a chance to mess with config filesI was just talking in general and not to you as a user. Have a nice day valvegrid.

---

### Post by valvegrid on 2011-10-27
Just a quick bit of feedback before I dash off, I signed into my wife's account just to try it as it hasn't been used and none of the /home config files have been touched and I'm getting the same there, so it look like I'll have to do a fresh install straight from 11.10.

I've never liked upgrading anyway. As a matter of interest, I've been using Ubuntu since 7.04 and this is the first time I've had any sort of real problem that I couldn't figure out my self. 

You also have a nice day, and I'll feedback later.

---

### Post by valvegrid on 2011-10-27
Well, I have just reinstalled and it all seems to be working now, so as I said earlier, I don't like upgrading. 

Now I'm off to reinstall all my applications.

Thanks for the help.

---

### Post by derapao on 2011-11-03
I had the same problem, and solved it by doing:

```
sudo apt-get install gnome-panel
```

I found the solution here:
[https://bugs.launchpad.net/alacarte/+bug/826049]("https://bugs.launchpad.net/alacarte/+bug/826049")

---

### Post by greasegum on 2011-11-14
I had the same frustrating problem mentioned above. I could access the alacarte main menu application, but I couldn't change or view any settings. Reinstallin alacarte didn't work, but running. **sudo apt-get install gnome-panel** did. 

Thanks to whoever posted this!

---

### Post by maufo on 2012-05-28
> **derapao said:**
> I had the same problem, and solved it by doing:

```
sudo apt-get install gnome-panel
```I found the solution here:
[https://bugs.launchpad.net/alacarte/+bug/826049](https://bugs.launchpad.net/alacarte/+bug/826049)

Fixed it. Thanks!

---

