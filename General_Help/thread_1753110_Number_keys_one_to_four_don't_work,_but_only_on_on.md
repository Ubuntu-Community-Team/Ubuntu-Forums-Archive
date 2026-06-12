---
title: "Number keys one to four don't work, but only on one account."
date: 2011-05-08
forum: General Help
---

### Post by Drakmor on 2011-05-08
Hi, I'm running kubuntu 10.04 with a few users on one system. On all the other accounts, the number keys work fine, but for me, I have to use the numpad for 1,2,3, and 4. I don't have an idea where to even start looking to fix this. I'm also not really sure what details to post, as I didn't change anything that would have affected the keyboard. I do know that the number keys did work about a week ago though. Also, I can use shift to get !,@, #, and $, and games detect if I alt+ one of the numbers too. Thanks!

---

### Post by enimeizoo on 2011-05-08
Hello,
You could try to see your xmodmap config with :
```
xmodmap -pk
```This shouldl give you the whole configuration of your keyboard. You will have to find your number keys in it. On my laptop they are lines 10 to 19, but you might have a different keyboard. 
You can use grep to filter the output.
```
xmodmap -pk | grep "(4)"
```This should give you only the line concerning the key number 4.
EDIT: since keys 1-4 don't work, this might not give you any result, but you can try to chek for the key number 5 for example, to see where the key numbers are, and then check the unfiltered output for these lines. You should pay attention to differences between lines concerning keys 1-4 and lines concerning 5-0.

You can also see what is happening when you hit the key with 
```
xev
```or
```
xbindkey -k
```

---

### Post by Drakmor on 2011-05-10
Hey, thanks for the tips. I'm really busy with school right now, otherwise I would have gotten back earlier. I tried the things you said, and it gave me a bunch of info that I have no idea what to do with, so I'm posting it here to see if you guys can tell me what it means:

Xev output for keys 1-4:
```
KeyRelease event, serial 31, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1176571, (395,476), root:(399,499),
    state 0x10, keycode 10 (keysym 0x31, 1), same_screen YES,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   8   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1179563, (395,476), root:(399,499),
    state 0x10, keycode 11 (keysym 0x32, 2), same_screen YES,
    XLookupString gives 1 bytes: (32) "2"
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   16  0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1180715, (395,476), root:(399,499),
    state 0x10, keycode 12 (keysym 0x33, 3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

FocusOut event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 34, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  2   32  0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 34, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1181483, (395,476), root:(399,499),
    state 0x10, keycode 13 (keysym 0x34, 4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1184331, (395,476), root:(399,499),
    state 0x10, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XmbLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3e00001,
    root 0x103, subw 0x0, time 1184427, (395,476), root:(399,499),
    state 0x10, keycode 14 (keysym 0x35, 5), same_screen YES,
    XLookupString gives 1 bytes: (35) "5"
    XFilterEvent returns: False
```
I think the stuff about focus is because I moved my mouse a bit too, but I'm not sure.

Xmodmap output about number key area:
```
 10         0x0031 (1)      0x0021 (exclam) 0x0031 (1)      0x0021 (exclam)
     11         0x0032 (2)      0x0040 (at)     0x0032 (2)      0x0040 (at)
     12         0x0033 (3)      0x0023 (numbersign)     0x0033 (3)      0x0023 (numbersign)
     13         0x0034 (4)      0x0024 (dollar) 0x0034 (4)      0x0024 (dollar)
     14         0x0035 (5)      0x0025 (percent)        0x0035 (5)      0x0025 (percent)
     15         0x0036 (6)      0x005e (asciicircum)    0x0036 (6)      0x005e (asciicircum)
     16         0x0037 (7)      0x0026 (ampersand)      0x0037 (7)      0x0026 (ampersand)
     17         0x0038 (8)      0x002a (asterisk)       0x0038 (8)      0x002a (asterisk)
     18         0x0039 (9)      0x0028 (parenleft)      0x0039 (9)      0x0028 (parenleft)
     19         0x0030 (0)      0x0029 (parenright)     0x0030 (0)      0x0029 (parenright)


```

Hopefully this means something that can help get this fixed!

---

### Post by enimeizoo on 2011-05-10
Okay, bad news is that your xmodmap output is fine. This is kinda bad news because that would have been really easy to solve...
xev's output is strange, thought. The xev window seems to loose focus when you press the key, so you don't have a keypress event (that explains why the keys don't work).  I just reproduced it by assigning shortcuts to a single key (without modifier). I think you somehow assigned shortcuts to keys 1..4 . 
If you just want to have your keys back, assign anything to these keys, kde will tell you that they are already in use and ask you to confirm. Then you just have to remove the shortcut you just made.
The proper way to do this would be by finding what you assigned to it, so that you can reassign the shortcuts (with alt+1 ... alt+4 ofr example). Since you have to search in every tab, it might be easier to find it by exporting your shorcuts in a file, searhing in this file and then importing the file back or something like that.

If I am right, it is not as bad as I thought. But lately a problem about the keyboard and xev got me a headache, so I imagined the worst. Actually, it ended up that the problem was the keyboard manufacturer who thought that a key that doesn't send a keycode was a good idea...

(edit) And if it is a shortcut problem, it is strange that you didn't notice that something happened. I would be curious to know what was assigned to it if I were you.

---

### Post by Drakmor on 2011-05-11
Sweet, that worked! I looked at my shortcuts, then remembered I put some Kmix volume shortcuts on !,@,#,and $. They didn't seem to work, and I guess they were causing this issue too. Thanks!

---

