---
title: "Ubuntu starts with no metacity and terminal and downloads folder open."
date: 2010-11-22
forum: General Help
---

### Post by BrockStrongo on 2010-11-22
Hi All,
    Every time I boot into Ubuntu, terminal is open, as is the downloads folder. It's not a big issue, just odd. This only started happening about a month ago. Nothing has changed in my startup applications or startup manager. 
    The other odd thing, occasionally at startup metacity is not running. I have to manually start it. I don't have emerald installed. 
Anyone else experiencing this?
Any suggestions for either problem?
Thanks in advance,

---

### Post by bonixavier on 2010-11-22
I don't know how to fix it, but you can get around it by typing (in the terminal or using Alt+F2, if it works) metacity --replace. Then you'll adjust your gnome-session to always run that command in the beginning of the session until you can find a more definitive solution. Open System > Preferences > Session Applications (or something like that, I don't know how they call it in English) and click add.
Put whatever name you want and the same command I said.

If it's just the lack of metacity, this will restore your usual gnome.

---

### Post by gary0 on 2010-11-22
Hi,
go to system - preferences - startup applications. Click the options tab and see if remember currently running application is ticked. If it is, untick it, if not then i don't know.... 
Gary

---

### Post by BrockStrongo on 2010-11-22
Thanks for the replies. "remember currently running applications is not ticked" thanks though. Another set of eyes never hurts.
 As for setting metacity to run at startup, that is a good workaround. It's just odd that I would have to do that as metacity is already part of the startup script. Oh well, like I said it's not a big deal.
Thanks a lot for the help. I always know I can turn to this forum for quick help.
Cheers

---

### Post by BrockStrongo on 2010-11-23
Alrighty, 
     The problem appeared to be originating in Compiz. For some reason compiz wasn't starting at boot time. I deleted the "compiz fusion icon" application and manually started compiz. Three reboots now and everything appears to be back to normal. 
   I'm wondering if the "compiz fusion icon" is causing some issues?
Any thoughts?
Cheers

---

