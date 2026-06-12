---
title: "Problems Running Firefox alongside with Swiftfox"
date: 2010-04-12
forum: General Help
---

### Post by LinuXGo on 2010-04-12
Hi, I've tried to run swiftfox alongside with firefox but to no avail and since they are both similar to each other, its almost difficult to seperate both of them to an indivdual browser. A user suggests me to create two new profile and create a shortcut for both browsers, enter their profile name then sync their data through Weave. In the process, this method isn't effective and I was lost at the mid-step, I did happen to complete the operation however, the browser won't allow the other browser to run without closing the one that's currently running.
 
How would I approach this issue of running both browser at the same time, I've done some research online but to no avail and the only fragments I've found was from swiftfox forum, basically introducing the same process as the one I've describled. Thanks for those who're reading this thread and anyone reply would be greatly considered.

---

### Post by lovinglinux on 2010-04-12
To start another browser simultaneously, used these commands:

```
firefox -P -no-remote
```

or

```
swiftfox -P -no-remote
```

The **-no-remote** part of the command tells the browser to start with another process, instead of another window of the same browser. The **-P** par of the code tells the browser to start with the Profile Manager. You can't use two instances of Firefox or Swiftfox with the same user profile. So if you want to run both simultaneously, you will need to create a separate profile for each browser.

What exactly are you trying to achieve by running two browsers simultaneously?

---

### Post by LinuXGo on 2010-04-13
Well, basically I'm using Swiftfox as an alternative to Firefox because due to its erratic behavior when viewing flash contents; page will completely freeze and shut down would be required. Hours later, I've seen your post about the problem of playing flash content with firefox 3.6.4pre and it's the exact solution that I was seeking for.

Anyways, I've already tried that method: I created a profile for each browser along with the name but the browser won't run together. A user online told me to also create a shortcut and sync both data to each other, I'm not sure if this a correct process... To lay out me steps carefully, I've created two profile called Firefox and Swiftfox, then if I run the command along with the name on a bash terminal. The browser will pop up and vice versa, but since that step has already been completed, I'm lost on what to do next? 

Thanks for your post earlier on and the thread you've replied.

---

### Post by lovinglinux on 2010-04-13
> **LinuXGo said:**
> Anyways, I've already tried that method: I created a profile for each browser along with the name but the browser won't run together. A user online told me to also create a shortcut and sync both data to each other, I'm not sure if this a correct process... To lay out me steps carefully, I've created two profile called Firefox and Swiftfox, then if I run the command along with the name on a bash terminal. The browser will pop up and vice versa, but since that step has already been completed, I'm lost on what to do next? 

Thanks for your post earlier on and the thread you've replied.
They should run together as long as you use **-no-remote -P**. Just to make sure there isn't anything wrong with Swiftfox, I just installed and launched it without closing my Firefox.

You could also launch the profile directly, without calling the Profile Manager with these:

```
firefox -no-remote -P "Firefox"
```

```
swiftfox -no-remote -P "Swiftfox"
```

Please note that the names inside quotes are coincidentally the name of each browser just because you gave those names to the profiles. Also, don't remove the quotes.

---

### Post by LinuXGo on 2010-04-13
Yes, if you're assuming that using the terminal to open those two browsers then its a success trail that I had already partaken. However, I wish to open them up from a launcher or from the menu panel instead of actually running through a terminal.

---

### Post by lovinglinux on 2010-04-13
> **LinuXGo said:**
> Yes, if you're assuming that using the terminal to open those two browsers then its a success trail that I had already partaken. However, I wish to open them up from a launcher or from the menu panel instead of actually running through a terminal.

Just replace the launchers commands with the ones from my previous post.

---

### Post by LinuXGo on 2010-04-13
> **lovinglinux said:**
> Just replace the launchers commands with the ones from my previous post.

 Could you elaborate on the sentence that you just wrote? Where's the previous post that you mentioned?

---

### Post by lovinglinux on 2010-04-13
> **LinuXGo said:**
> Could you elaborate on the sentence that you just wrote? Where's the previous post that you mentioned?

Go to "System >> Preferences >> Main Menu", right-click on the Firefox launcher and select Properties or something like that (I'm using KDE so give some slack), then replace the field labeled "command" where you read **firefox %u** with **firefox -no-remote -P "Firefox"**. You can do the same with launchers on your panel.

---

### Post by LinuXGo on 2010-04-14
Great, the method that you replied worked very smoothly and I greatly thank you for the assistance that you provided. I've also discover my mistake, I didn't actually input the phase "fire%u" and it led to my failure however I'll use your method of averting this problem ever occur again.  Thank you very much.  :)

---

