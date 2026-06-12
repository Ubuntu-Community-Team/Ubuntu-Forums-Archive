---
title: "Java application opens without window content"
date: 2010-10-06
forum: General Help
---

### Post by MountainX on 2010-10-06
I"m running 10.04 on a netbook. I switched my Java look and feel to Nimbus and now my java application opens with most of the buttons and window content missing. The main menu is there, but otherwise the main form is mostly blank. If I restart the application (not my computer) 2-3 times, the problem is resolved until the next time I have to launch the java app. I did not see this issue before changing the look & feel setting for Java. But the GTK l&F doesn't work for other reasons, so I was forced to make a change.

Any ideas for resolving this? I'm running compiz and I know the blank windows in Java apps was a common problem a while back. I'm not sure if what I'm seeing is related to that old problem or is something different.

---

### Post by MountainX on 2010-10-07
I found some new links:  
[http://www.hydronitrogen.com/723/linux-window-manager-java-problems-blank-window-fix/](http://www.hydronitrogen.com/723/linux-window-manager-java-problems-blank-window-fix/) 
[https://bugzilla.redhat.com/show_bug.cgi?id=509301](https://bugzilla.redhat.com/show_bug.cgi?id=509301) 

wmname looks interesting but I'm not sure how to use it or if it applies in this situation. Can anyone advise?

---

### Post by npgall on 2010-11-25
Hi MountainX,

I have the same issue, and one of my colleagues also. Started happening since I upgraded to Ubuntu 10.10. On Ubuntu 10.04 it was fine for me though. It looks like the blank java+compiz window from a few years ago, but it affects only popup dialogs, and then only occasionally.

I'm not sure if this is caused by the new version of compiz, or the new version of Java in 10.10. I have tried Sun JDK and OpenJDK.

The app is IntelliJ IDEA 9.0.4 with Nimbus L&F selected.
Compiz 1:0.8.6-0ubuntu9.1
Sun JDK 6.22-0ubuntu1~10.10   (java -version = "1.6.0_22")
OpenJDK 6b20-1.9.1-1ubuntu3   (java -version = "1.6.0_20")

---

