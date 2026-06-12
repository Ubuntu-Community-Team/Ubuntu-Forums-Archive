---
title: "Conky does not start at startup even with 30 sec sleep!"
date: 2010-01-21
forum: General Help
---

### Post by chinmaya_n on 2010-01-21
Yes,
Conky does not start during start up
I used this script, It has execute permission also!
[COLOR="DarkRed"][B]
#!/bin/bash
sleep 30 && conky;[/B][/COLOR]

But it did not start! What is the problem!
It works manually when i run that script!
[U][COLOR="Plum"]
Note:[/COLOR][/U] It is not working in the background also at startup as i checked it -
When is run [COLOR="DarkRed"]**killall conky**[/COLOR] it showed [COLOR="DarkRed"]**No such process**[/COLOR]

---

### Post by Brandon Williams on 2010-01-21
Is there anything in your ~/.xsession-errors file to indicate that there was a problem with the script? If not, then try changing the #! line to '#!/bin/bash -x', and then look in ~/.xsession-errors after you log in. There should be some indication in ~/.xsession-errors that the script is being run. If the script is being run and not producing any errors, then I'm not sure what to suggest next.

---

### Post by chinmaya_n on 2010-01-22
I'm sorry :(

Just now I checked it again with the 30 sec delay! It worked......!
But I'm sure it didnt work the last time!
Any way It was my dumbness ! 

Thanx for ALL and Specially 2 "[Brandon Williams]("http://ubuntuforums.org/member.php?u=744208")"

---

