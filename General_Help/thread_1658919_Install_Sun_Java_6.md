---
title: "Install Sun Java 6"
date: 2011-01-03
forum: General Help
---

### Post by jock mackay on 2011-01-03
I am brand new to Linux (please be understanding) running Ubuntu 10.4 on a Dell Notebook. I have read so many posts on this subject that my eyes are crossing, but I remain unsure about how to proceed. 
So far I have made the Java version supplied inactive (I think), and have used the terminal to defuse a  wireless card incompatibility with Firefox, so I have gained some familiarity with the terminal operation, and software situation.
I would appreciate any help I can get to install Sun Java.

---

### Post by mikewhatever on 2011-01-03
Sun java 6 is in the Canonical's partner repository. You'll need to add that repository to your software sources, then install sun-java6-jre, and if you need the plugin, then also sun-java6-plugin.
You can enable the partner repository from System->Administration->Software Sources, Other Software tab.

---

### Post by tredegar on 2011-01-03
Well, you can do it the "complicated" way by downloading java from sun's site and following their instructions to install it, or you can do it the simple way, System- Admin -Synaptic, search on sun-java6 then select **sun-java6-jre** for installation.

If it is not listed, Open Synaptic, go to Settings, Repositories, and make sure all are selected on the Ubuntu Software" Tab (Canonical, Community, Proprietry Etc). Close that window.

Then click Reload, so the contents of the added repos are read and indexed. Then  search again for **sun-java6-jre** and install it.

Edit, mikewhatever, you are right, he needs **[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner** (on the second tab) enabling.

Then click Reload, then search, then install.
/Edit

---

### Post by jock mackay on 2011-01-03
One thing at a time for me, enabling ................I am at the right place, and see  [B][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner, how do I enable?
[/B]

---

### Post by jock mackay on 2011-01-03
Sorry about the bold type .............. not sure where that came from either!

---

### Post by howefield on 2011-01-03
Go to System > Administration > Software Sources > Other Software tab and place a check next to the line that says Canonical Partners. (probably the first line)

Press OK, then the Reload button.

Search for and install sun-java6-fonts sun-java6-jre and sun-java6-plugin

---

### Post by gandaran on 2011-01-03
> **jock mackay said:**
> One thing at a time for me, enabling ................I am at the right place, and see  [B][http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner, how do I enable?
[/B]
tick the little left box and close then click the reload button to update package list, you will now find sun-java6-plugin from the list.

---

### Post by jock mackay on 2011-01-03
No OK button Got Add, Edit, Remove, but no OK.

---

### Post by howefield on 2011-01-03
> **jock mackay said:**
> No OK button Got Add, Edit, Remove, but no OK.

Apologies, it is a close button that you need to press, not OK.

---

### Post by tredegar on 2011-01-03
You have a list of [http://.](http://.)... lines
To the left of each line is a little box (maybe resize your window?).
Click on the little box to put a checkmark in it to enable it.
Click again to remove the tick to disable it.
Then click Close, Then Reload.

---

### Post by mick222 on 2011-01-03
you dont need to press ok just tick the box then close when you open synaptic search then do as mikewhatever says in his post.Also you should remove the icedtea plugin if it is installed.

---

### Post by jock mackay on 2011-01-03
Hey, guys, thanks for your patience. I have stumbled along, and think I have installed Sun java6
Please tel lme how I can check it is installed, and is the active choice for java.

---

### Post by tredegar on 2011-01-03
Open up firefox, and go to about:plugins 
Edit:
Open up firefox, and go to about[colon]plugins (Stupid smilies)
Scroll down.

---

### Post by howefield on 2011-01-03
> **jock mackay said:**
> Please tel lme how I can check it is installed, and is the active choice for java.

Run the command..

```
sudo update-alternatives --config java
```

---

### Post by jock mackay on 2011-01-03
OK, I have run the command in the previous post, and I first chose the auto option, and then the manual option, but neither seemed to click with jmeeting.com. 
When I look at my installed software I see Icetea, and also Sun Java.

How do I make the system chose between them?

This looks tantalising close to being sorted out!

---

### Post by tredegar on 2011-01-03
> How do I make the system chose between them?
Like howefield said at post #14

---

### Post by gandaran on 2011-01-03
> **jock mackay said:**
> OK, I have run the command in the previous post, and I first chose the auto option, and then the manual option, but neither seemed to click with jmeeting.com. 
When I look at my installed software I see Icetea, and also Sun Java.

How do I make the system chose between them?

This looks tantalising close to being sorted out!
it would be better just to remove the icedtea plugin then the sun-java plugin would work without doing anything else.

---

### Post by mikewhatever on 2011-01-03
Since you've installed sun-java, why not remove icetea now. And I really mean remove, not disable make inactive or anything else, but uninstall.

---

### Post by jock mackay on 2011-01-03
My head hurts, and the battery is running low, so I am going to take a break. Not given up, but pausing to clear the head. I will return to this tomorrow, UK time.

Thanks for everything so far.

---

### Post by jock mackay on 2011-01-04
I now have sun java working. Thank you all for your help.

As somebody who is new to Ubuntu I am involved in climbing up the slopes of a steep learning curve, and an hanging on by the fingernails. It is good to know there is a safety net below me.

---

### Post by mikewhatever on 2011-01-04
Glad to know it worked for you. Just a friendly advice, don't wait till your head aches next time, the community is here to help, so just ask.

---

