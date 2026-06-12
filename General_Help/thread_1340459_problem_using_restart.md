---
title: "problem using restart"
date: 2009-11-28
forum: General Help
---

### Post by Gatorade on 2009-11-28
I've got a toshiba portege laptop that I just installed Ubuntu 9.04 on.

The problem I'm experiencing is when ever I try to use the restart function, it shuts down , but it doesn't come back on fully. I can still hear something going on , so I know its turned off completely. it just shows a black screen.

I have to hold the power button down 'til it shuts off completely, and then start it again by pushing the power button.

Its not really a problem if I just want to turn it off , since that works ok.
but if I want to make some changes and just restart , that's when it  just hangs on the restart.

any ideas on why this is happening?

---

### Post by tekkidd on 2009-11-28
try going in and rebooting on the system 

or 

in the terminal: reboot

---

### Post by Gatorade on 2009-11-29
where's the reboot option in system?

I don't see that option.

reboot in terminal didn't work, hangs just the same. that's kind of a troublesome way of doing it anyways.
it'd be much easier if I could just use the restart.

---

### Post by garvinrick4 on 2009-11-29
sudo shutdown -r now     for reboot


 sudo shutdown -h now      for shutdown



Go to Configuration Editor open Apps got to indicator-session
and check the value box and it will kill timer in shutdown or 
reboot from GUI. Just reboots or shutsdown.


Alt/F2   and type gconf-editor hit enter will get you there if not
in system tools in GUI.

---

### Post by Gatorade on 2009-11-29
not exactly sure if I did it correctly( I think I did) , but I tried that and it still didn't work for me.

alt/F2 brings up a box that says run application.

I typed in what you said and got to the configuration editor.
opened apps, but I didn't see anything that said indicator session.

there was something that said indicator-applet. is this what you meant?
to the left of the value box it said dummy_value
do I just check that box and close the window?

well, that's how I tried it anyways and it didn't work.

I tried this as well and it didn't work

"sudo shutdown -r now for reboot"


didn't bother to try the "shutdown -h"  since there's no problem with shutting it down. Its just a problem if I wanted to do a restart. I can shut it down , wait , and then turn it back on. but that's slower, than if I just hit restart and let it turn off and come back on like its supposed to.

---

### Post by litspliff on 2009-11-29
what happens when you:
**sudo init 6**
at a terminal?

same result?

---

### Post by Gatorade on 2009-11-29
yeah, same result.

I'm wondering if its possibly a hardware problem .

---

### Post by garvinrick4 on 2009-11-29
"sudo shutdown -r now"   without qoutes.


I just looked again and it is indicator-session, look aqain just in case.  Open the APP arrow
and go down to the   i's   and see if it is there. 


If that terminal command does not reboot you then something is terrible wrong.

---

### Post by Gatorade on 2009-11-29
I followed what you said , it says indicator -applet.

I checked another computer, and it also says indicator-applet

I can't be bothered with it.
doesn't look like its going to work and its not worth wating any more time on it.

thanks anyhow.

---

