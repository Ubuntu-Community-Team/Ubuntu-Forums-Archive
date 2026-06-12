---
title: "How to exchange left/right mousekey in 10.10 using xorg.conf.d?"
date: 2011-01-16
forum: General Help
---

### Post by pheidrias on 2011-01-16
Hello Community,

I have a strange problem, setting up my mouse(s) to be used lefthanded.
I know, that there is some GUI option, but I also need to set up other non-lefthanded devices, so I need full control of which device is configured in which way ;-).

When I try something like:

```

Section "InputClass"
        Identifier "Microsoft IntelliMouse"
        MatchIsPointer "true"
        MatchIsKeyboard "false"
        Option "ButtonMapping" "3 2 1 4 5 6 7 8 9"
EndSection

```

there won't be a change in the behaviour of my mouse.
Instead when I try         Option "ButtonMapping" "1 3 2 4 5 6 7 8 9", the right and middle mouse buttons are exchanged.

The xinput method works
> 
xinput --set-button-map "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)" 3 2 1 4 5 8 9

but fails to be persistent and also produces some problems, when USB-devices are (un-)plugged.

So what is the problem with xorg.conf.d?
I also tried different mices without any success...

Any suggestions?
Thanks!

---

