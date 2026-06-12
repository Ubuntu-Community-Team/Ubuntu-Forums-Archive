---
title: "ubuntu 12.04 - shift key not working - very bizzare"
date: 2012-10-03
forum: General Help
---

### Post by juliohm on 2012-10-03
as you can see, i am typing this without any capital letters. it's very hard to use the shift key when it doesn't work properly.

in fact, for reasons i am unable to gather, both shift keys on my keyboard stopped working correctly -- right in the middle of a gnome session.

in fact, pressing left shift will launch calculator and thunderbird simultaneously -- while right shift will cause my browser window to return to its default home page.

yes it's very bizzare. i am desperately looking for a solution, but am unable to find a post here that helps.

so, i dearly ask for your help, since i don't know what to do before resorting to re-install everything.

as far as i can tell, the keyboard mapping seems to be royally screwed up. i can run 'xev' on the command line and check for x events

the following is the result of pressing the right shift key

```
KeyPress event, serial 30, synthetic NO, window 0x2e00001,
    root 0xc4, subw 0x0, time 541310, (117,-17), root:(1164,63),
    state 0x10, keycode 180 (keysym 0x1008ff18, XF86HomePage), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False
```


... and the following is the result of pressing the left shift key

```
KeymapNotify event, serial 35, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0  
```

as we can see the key mapping is all messed up. other threads with similar issues found their problem to be compiz and resetting, reinstalling, reconfiguring worked for them.

unfortunatelly, none of those worked for me. i tried removing compiz entirely

```
apt-get purge compiz-core
```

but nothing seems to work. rebooting does not work. changing the keyboard layout does not work.

i am stuck, so in a final desperate move, i am asking for help here.

thanks in advance.

---

### Post by juliohm on 2012-10-03
folks, nevermind... i tested with another keyboard - same make and model - and it worked fine.. i guess mey kbd is toasted.

thanks anyway.

-- that was fast.

---

