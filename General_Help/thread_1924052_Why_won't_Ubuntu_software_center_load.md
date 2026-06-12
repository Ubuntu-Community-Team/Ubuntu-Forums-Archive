---
title: "Why won't Ubuntu software center load?"
date: 2012-02-11
forum: General Help
---

### Post by SFBrother on 2012-02-11
Hi.
When I try to go to the software center, it opens up, but nothing shows up on the screen. Just a white box. I don't know why it is doing this. Can ya help me out?

---

### Post by jerrrys on 2012-02-11
Open a terminal and enter:

sudo apt-get update

Will the SWC work now?  Did you get any errors?

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> Open a terminal and enter:

sudo apt-get update

Will the SWC work now?  Did you get any errors?

I did that. And it still won't work.

---

### Post by jerrrys on 2012-02-11
Sorry

[https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)

Please post all questions

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> Sorry

[https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)

Please post all questions

Right. I got the terminal up, and put in that code. Software center will still not work.

---

### Post by jerrrys on 2012-02-11
Did that command give you and errors?

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> Did that command give you and errors?

No. There were no errors, I think it did it's thing. It game a list of websites and links in a way, and at the end, it said Done.

---

### Post by jerrrys on 2012-02-11
in terminal:

sudo apt-get upgrade  && sudo apt-get clean

---

### Post by cortman on 2012-02-11
USC is known to be a bit buggy. Unless the other folks here have something else in mind, I'd uninstall and reinstall it. That's fixed it for most that I've seen.

```
sudo apt-get remove software-center
sudo apt-get install software-center
```

---

### Post by jerrrys on 2012-02-11
You beat me to it cortman :)

---

### Post by SFBrother on 2012-02-11
> **cortman said:**
> USC is known to be a bit buggy. Unless the other folks here have something else in mind, I'd uninstall and reinstall it. That's fixed it for most that I've seen.

```
sudo apt-get remove software-center
sudo apt-get install software-center
```

I tried this. It successfully uninstalled, and I successfully installed it again. Still, when I open it, its a white box.

---

### Post by jerrrys on 2012-02-11
OK, once again in terminal enter:

software-center

Maybe get some errors now?

---

### Post by bluexrider on 2012-02-11
I would try ```
sudo rm -rf ~/.config/software-center
```
then try it again

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> OK, once again in terminal enter:

software-center

Maybe get some errors now?

No error. It just opened it up. Showing nothing but the white box.

---

### Post by jerrrys on 2012-02-11
Try bluexrider's suggestion

---

### Post by SFBrother on 2012-02-11
> **bluexrider said:**
> I would try ```
sudo rm -rf ~/.config/software-center
```
then try it again

When I did this, it just brought me to. Nothing else happened.
>

---

### Post by savanna on 2012-02-11
Try "sudo aptitude safe-upgrade"

---

### Post by SFBrother on 2012-02-11
> **savanna said:**
> Try "sudo aptitude safe-upgrade"

Command not found.

---

### Post by jerrrys on 2012-02-11
In terminal:

sudo dpkg -r software-center

sudo apt-get install software-center

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> In terminal:

sudo dpkg -r software-center

sudo apt-get install software center

Still. It uninstalls successfully, and installs successfully, but when I open it, I see nothing but white. Do you think that this is a bug with Ubuntu, that they can fix this? Maybe release an update for this bug? 

Do you think restarting my computer will do anything?

---

### Post by jerrrys on 2012-02-11
in terminal:

sudo software-center

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> In terminal:

sudo dpkg -r software-center

sudo apt-get install software center

After I did this, it says it is installed, but now I can't find it. I checked the dash home, and the apps, and typed it in looking for it. Nothing shows up. But the terminal says it is installed.

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> in terminal:

sudo software-center

Hey, It's working now. I would like to thanks you two for helping me (A newb) with this little problem. You were helpful, and you did not give up easily. Thanks for your help.

---

### Post by jerrrys on 2012-02-11
Did you add that "dash" that i missed in my command?

sudo apt-get install software-center

also two last commands

sudo dpkg --configure -a

sudo apt-get install -f

---

### Post by jerrrys on 2012-02-11
There are some bug reports out there:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+white+blank+box&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+white+blank+box&sa=Search&cof=FORID:9)

A work-a-round for the moment would be install Synaptic Package Manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

sudo apt-get install synaptic

---

### Post by bluexrider on 2012-02-11
one last thing to try would to move the software center cache and try one more time

```
sudo mv ~/.cache/software-center ~/
```

---

### Post by cortman on 2012-02-11
Whew. That was one weird set of errors! Good its working now.
I second Jerry's Synaptic recommendation. Excellent program, user friendly enough to be easy on new users and yet powerful enough to satisfy CLI afficiandos.

---

### Post by jerrrys on 2012-02-11
I missed your post#23.  So glad to hear that.  You may still want to load synaptic package manager for backup, if it happens again.

And welcome to the forums :D

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> There are some bug reports out there:

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+white+blank+box&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=software+center+white+blank+box&sa=Search&cof=FORID:9)

A work-a-round for the moment would be install Synaptic Package Manager

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic&sa=Search&cof=FORID:9)

sudo apt-get install synaptic

What should I do when I install synaptic Package?

---

### Post by jerrrys on 2012-02-11
It can be used as a replacement for SWC, if needed.  Check out the above synaptic link.  It will also appear in dash.

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> It can be used as a replacement for SWC, if needed.  Check out the above synaptic link.  It will also appear in dash.

Still a bit curious. Should I install anything using Synaptic? I got it installed, and don't know what to install. There is a lot of things there, and I don't think I need it all.

---

### Post by jerrrys on 2012-02-11
Synaptic comes with a boat load of options for the advance user.  In your case it can simply be used to install packages, just like the software center.  If it should break again.  Its really worth getting to know.

Examples:

It can upgrade your system if your update manager stops working.

It can clean out old/unused packages

It will give you detailed package information

You can edit software sources from within it.

and on and on

---

### Post by SFBrother on 2012-02-11
> **jerrrys said:**
> Synaptic comes with a boat load of options for the advance user.  In your case it can simply be used to install packages, just like the software center.  If it should break again.  Its really worth getting to know.

Examples:

It can upgrade your system if your update manager stops working.

It can clean out old/unused packages

It will give you detailed package information

You can edit software sources from within it.

and on and on

So, basically anything I want to do with a program or app, or software, it can be updated, removed, and stuff from here?
So it's like a backup?

---

### Post by raja.genupula on 2012-02-11
No not a backup , its better than software center . 
* In software center you cant able to fix broekn pkg's but synaptic can do that.

* synaptic can flash faster than software center .

* dependencies you can easily get from synaptic .

---

### Post by SFBrother on 2012-02-11
> **raja.genupula said:**
> No not a backup , its better than software center . 
* In software center you cant able to fix broekn pkg's but synaptic can do that.

* synaptic can flash faster than software center .

* dependencies you can easily get from synaptic .

Alright. So, can I get software from there? Because when I closed the terminal, the same problem is happening. I'm not liking the software center, and I think it really needs an update to make it better.
EDIT: I can only get into it from the terminal. Well, that is interesting.

---

### Post by raja.genupula on 2012-02-11
Yes you can get software from synaptic but here i must say one point .

In software center installing a package means , you gonna search that & you will install . 

In synaptic , you have to select that package along with require dependencies and then only that software can run fine . 

I know its a problem in synaptic but it gives idea about to run an application what things we need . 

ha ha ha we have a Advantage in that too . :) :)

---

### Post by raja.genupula on 2012-02-12
>  I can only get into it from the terminal. Well, that is interesting 

sorry i am unable to get this , here what is this "it" ? synaptic or something else ?

---

### Post by SFBrother on 2012-02-12
> **raja.genupula said:**
> sorry i am unable to get this , here what is this "it" ? synaptic or something else ?

I for got to say what. But I can only get into software center from the terminal.

---

### Post by raja.genupula on 2012-02-12
what happening while you're trying to get it from the icon directly ?

---

### Post by SFBrother on 2012-02-12
> **raja.genupula said:**
> what happening while you're trying to get it from the icon directly ?

I open it up, and it is blank. Just all white. Nothing loads, nothing pops up, just blank.

---

### Post by jerrrys on 2012-02-12
> **SFBrother said:**
> So, basically anything I want to do with a program or app, or software, it can be updated, removed, and stuff from here?
So it's like a backup?

Synaptic is like SWC on steroids.

---

### Post by raja.genupula on 2012-02-12
> **SFBrother said:**
> I open it up, and it is blank. Just all white. Nothing loads, nothing pops up, just blank.

Ok , have you did purging software center 

i mean ```

sudo apt-get remove --purge software-center
sudo apt-get clean
sudo apt-get install software-center
```

have you tried ?

---

