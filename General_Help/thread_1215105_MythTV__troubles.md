---
title: "MythTV  troubles"
date: 2009-07-16
forum: General Help
---

### Post by davisw8 on 2009-07-16
I tried installing mythtv by typing in the terminal sudo apt-get install mythtv and then svn co [http://svn.mythtv.org/svn/branches/release-0-21-fixes/](http://svn.mythtv.org/svn/branches/release-0-21-fixes/). I am so new to ubuntu and so confused as to what to do next or if im even doing the right thing in the first place. I downloaded the pdf installation instructions but its 100 some pages. In other words I didnt read it. Anyone want to give some legit help? Thanks in advance.

---

### Post by issih on 2009-07-16
It is much easier to install mythtv into ubuntu using the mythbuntu packages.

So uninstall what you have done so far then do the following.

Install the package mythbuntu control centre, the following in terminal will do it for you:

```
sudo apt-get install mythbuntu-control-centre
```

Alternatively just find it in synaptic package manager.

Once that is installed, go to System->Administration and launch the control centre.

In that program select the "roles" you want to have on that machine and ensure that the mysql service is enabled (if you want remote front ends) and hit apply. That will install all the myth tv packages you need.

Once its installed you have to go to System->Administration and select the mythtv backend setup option.

In there you will need to work through everything to set myth tv up to get it working (which is where your manual might be useful, but its not all that bad really, just a bit quirky)

Once the backend is configured, just start the front end (under Applications->Sound and Video) and you should be up and running.

Once you are at that level, you can ask any other questions that are bugging you :)

Hope that helps

---

### Post by davisw8 on 2009-07-23
thanks a lot for the help i really appreciate it. Heres my new dilemma. i installed mythtv but when i go to mythbuntu control centre and launch the configuration thing i have no idea what to do. all i want to do is use this program but my inabiity to figure this stuff out kills me

---

### Post by trwww on 2009-07-24
Perhaps if you tell us what it is you are trying to do. Break it down in to steps. Whats the very next thing you need to do?

Then perhaps you will get some instructions on how to do it. Remember what you did, so the next time it will be easier to figure out how to do the next thing you need to do on your own. If you cant figure it out, come back and describe the issue you are having with the next thing you are trying to do.

Also, The manual might be big, but its there for a purpose so if you are ever going to seriously use Mythbuntu you're going to have to read it :0)

---

### Post by adza on 2009-07-25
Hi there, i'm also trying to figure this one out.. i have a Qleadtech DTV2000H card installed and working (TV works in windows partition). When i attempt to run a channel scan however, i get no signal stregnth at all and it doesn't find any channels.. how do i 'activate' this card in mythbuntu?

---

