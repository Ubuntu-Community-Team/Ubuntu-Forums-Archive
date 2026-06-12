---
title: "firefox assertion failed error"
date: 2010-10-05
forum: General Help
---

### Post by alenis on 2010-10-05
Since several weeks Firefox often stop working displaying a window  "assertion failed" with the following content:

```

ASSERT: node must have _DOMElement set
Stack Trace: 
0:TV_V_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],45)
1:removeFolderChildren(287575)
2:LS_deleteLivemarkChildren(287575)
3:LLL_runBatched([xpconnect wrapped nsIFeedResult])
4:runInBatchMode([object Object],[xpconnect wrapped nsIFeedResult])
5:LLL_handleResult([xpconnect wrapped nsIFeedResult])
6:handleResult([xpconnect wrapped nsIFeedResult])
7:FP_sendResult()
8:FP_endDocument()
9:onStopRequest([xpconnect wrapped (nsISupports, nsIRequest, nsIChannel)],null,0)
10:FP_onStopRequest([xpconnect wrapped (nsISupports, nsIRequest, nsIChannel)],null,0)
11:onStopRequest([xpconnect wrapped (nsISupports, nsIChannel, nsIHttpChannel, nsIRequest)],null,0)
12:LLL_onStopRequest([xpconnect wrapped (nsISupports, nsIChannel, nsIHttpChannel, nsIRequest)],null,0)


```

Pressing OK closes the window which, unfortunately, often appears again immediately after for 10/15 times. This is extremely annoying and actually makes Firefox not usable anymore. Does anybody else have the same problem? What can I do to eliminate it? 
Thanks

---

### Post by lovinglinux on 2010-10-05
Looks like a problem with Live Bookmarks or some Feed extension.

Please start Firefox in safe mode and check if the problem persists.

See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by alenis on 2010-10-06
Thanks for your help. The problem seems to be connected with bookmarks. I made a backup of my bookmarks, then removed all of them, but the problem was still there (although the alert box was smaller). Then I restored the boolmarks and a very huge alert box appearead. 
Eventually, after deleting "places.sqlite" from the profile, the problem seems to be solved.

---

### Post by lovinglinux on 2010-10-06
> **alenis said:**
> Thanks for your help. The problem seems to be connected with bookmarks. I made a backup of my bookmarks, then removed all of them, but the problem was still there (although the alert box was smaller). Then I restored the boolmarks and a very huge alert box appearead. 
Eventually, after deleting "places.sqlite" from the profile, the problem seems to be solved.

You could try to restore a backup of your bookmarks using the Bookmarks manager. Just make sure you restore a backup created before the problem appeared.

---

