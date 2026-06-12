---
title: "Eclipse cdt?"
date: 2009-10-30
forum: General Help
---

### Post by boom2k1 on 2009-10-30
Is eclipse cdt broken in 9.10?

---

### Post by Sand Lee on 2009-11-06
Yep, they [removed the package]("https://bugs.launchpad.net/ubuntu/+source/eclipse-cdt/+bug/461995") because it isn't updated. Good news is you can still get CDT installed. 


[LIST=1]
[*]Open Eclipse
[*]Go to Help => Install New Software
[*]Insert: [http://download.eclipse.org/tools/cdt/releases/galileo](http://download.eclipse.org/tools/cdt/releases/galileo) into the "Work with" field
[*]The rest is self-explanatory...
[/LIST]

---

### Post by crazy ivan on 2009-12-20
Somehow for me it was not as self-explanatory :confused:

Doing this I got

```

An error occurred while collecting items to be installed
session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Collect, operand=, action=).
No repository found containing: osgi.bundle,org.eclipse.cdt,5.1.0.200906161748
No repository found containing: ...

```

Seemingly this happened to other people before: [http://www.eclipse.org/forums/index.php?t=rview&goto=488161&th=154911]("http://www.eclipse.org/forums/index.php?t=rview&goto=488161&th=154911")

But then I remembered that I tried to save some time by copying the old settings from my 3.4 release to my new "~/.eclipse" configuration folder. 

```

rm -r ~/.eclipse

```

finally solved the problem for me.. But now all my Update sites were gone. Luckily I found most of them on

[http://ekkescorner.wordpress.com/eclipse/update-sites/](http://ekkescorner.wordpress.com/eclipse/update-sites/)

Now the nasty "button hangs" bugs from 3.4 are gone, pydev debugs properly and photran is way better :guitar:

---

