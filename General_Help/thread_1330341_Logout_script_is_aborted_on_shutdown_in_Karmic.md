---
title: "Logout script is aborted on shutdown in Karmic"
date: 2009-11-18
forum: General Help
---

### Post by Dan_N on 2009-11-18
I use login/logout-scripts to synchronize home folder between computers. On Ubuntu 8.04 this worked perfect. I placed calls to my scripts in &#8220;/etc/gdm/PreSession/Default&#8221; and &#8220;/etc/gdm/PostSession/Default&#8221;. The &#8220;PostSession-call&#8221; also worked fine on shutdown.

On Karmic my scripts are aborted or &#8220;run ahead of&#8221;. I have done some testing and this seems to be the behavior on Karmic:


[LIST]
[*] Script called from &#8220;/etc/gdm/PreSession/Default&#8221;: The login completes in parallel with my script. This means that the user may start working on a document that is still not updated.
[/LIST]

[LIST]
[*] Script called from &#8220;/etc/gdm/PostSession/Default&#8221;:  This works fine on logout but not on shutdown. The script is aborted half way through on shutdown.
[/LIST]

[LIST]
[*]By curiosity a placed a call to my script in &#8220;/etc/rc.local&#8221;:  Now the script still halts on shutdown but is resumed on next boot, which is as bad for my functionality as &#8220;abort only&#8221;.
[/LIST]
 
Is there a way around this? 

I need to be confident with that the scripts run all the way otherwise the user data get totally messed up.

---

