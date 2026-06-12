---
title: "screen postition nvidia ubuntu 12.04"
date: 2012-05-03
forum: General Help
---

### Post by anyone2009 on 2012-05-03
Hi guys I posted a thread about my problem tow weeks a go and I'm sorry I didn't see the replys .. 
[http://ubuntuforums.org/showthread.php?t=1959610](http://ubuntuforums.org/showthread.php?t=1959610)
any way my problem is ... 

when I open ubuntu the screen position is to the left You can see the attached photos in the previous thread  to know what I mean ..
When I press AUTO/SET button on my LG W1943ss witch adjust the screen position it's become OK..

But when I restart my computer And open my windows 7 or even in the boot stage the screen become to the right and I have to press AUTO/SET button again to adjust the position of the screen ..

well .. the last reply in the previous thread by grahammechanical (thanks by the way :) ) was .. 
> You say that you have installed the Nvidia driver, have then tried to use the Nvidia X-Server Settings utility?

You will find it by opening the Dash and searching for Nvidia. When the utility has loaded look for the name of your graphics card.

You might see something like GPU 0 -(Geforce GT240) followed by Thermal Settings, PowerMizer and DFP-0-(name of your monitor).

Click on DFP-0-(name of your monitor) and then look for GPU Scaling Method. You might need to tick the box that says Centred.

Regards.

But when I try to apply this solution I don't find DFP Option like what you see in the attached  file so Do you have any Idea why I can't have this option ?

---

### Post by anyone2009 on 2012-05-04
any help guys

---

### Post by anyone2009 on 2012-05-04
guys please how can I get DFP option ?

---

### Post by DenysT on 2012-05-04
You have to click on the XServer display configuration to get to that option.

---

### Post by anyone2009 on 2012-05-05
Well Thanks DenysT for your reply ,but honestly it doesn't work .. 
anyway I make a workaround  :
First install ARandR from the software center .. then open it and click save and save it with any name .. 
open startup applications and add new app in the command field write the following .. 
sh "/home/(your username)/.screenlayouts/(the file name)"
and press ok .. now when you just login every thing will look fine .. 
in my case I write the command as follows 
sh "/home/mohammed/.screenlayout/moh.sh"

good luck everyone

---

### Post by pqwoerituytrueiwoq on 2012-05-05
did you try saving to xconfig file?
you can try putting y script into /etc/rc.local

---

### Post by anyone2009 on 2012-05-05
I tried every thing but it's seems the only solution till now :)

---

