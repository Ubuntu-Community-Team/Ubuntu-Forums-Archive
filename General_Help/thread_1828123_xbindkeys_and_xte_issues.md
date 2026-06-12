---
title: "xbindkeys and xte issues"
date: 2011-08-18
forum: General Help
---

### Post by SwissBushIndian on 2011-08-18
I'm having a really hard time with xbindkeys and xte. I use it to get all my buttons on my performance mouse mx to work, which works like a charm. Now I thought: well why not use it to get my media buttons from my laptop, which I use in a dock at home, to work using my normal keyboard by sending the same keycodes through a key combination.

This has worked so far, and still does. It's what gets my mouse buttons to work:

```

#expose
"xte 'keydown Control_L' 'key F8' 'keyup Control_L'"
 b:10

#back
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L'"
 b:8

#forward
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L'"
 b:9

#desktop1
"xte 'keydown Control_L' 'keydown Alt_L' 'key 1' 'keyup Control_L' 'keyup Alt_L'"
 b:13

```

This is what I've been trying to get working since yesterday, which doesn't work:

```

#Volume Mute
"xte 'key XF86AudioMute'"
 Control_L+F10

```

nor does this:

```

#Volume Mute
"xte 'key 0x1008ff12'"
 Control_L+F10

```

Or any other wild combination of stuff, using control as a modifier instead of specifying Control_L etc. etc.. I've practically tried everything, even this:

```

"xte 'keydown Control_L' 'key F10' 'keyup Control_L'"
 XF86AudioMute

```

Which works, but is kinda sketchy. I have to rebind the combination in KDE, which is alright, but if I use this, the graphics are messed up and it only works sometimes. When bound correctly and used only on the laptop, everything works great.

More crazyness to show you that something isn't quite alright:

```

"xte 'keydown Control_L' 'keydown Alt_L' 'key 1' 'keyup Control_L' 'keyup Alt_L'"
 Control + b:1

```

works!

```

"xte 'key XF86AudioMute'"
 Control + b:1

```

Doesn't work.

So now what?

I've read the manpage about 50 times, I've looked the example files of xbindkeys, which specifically has examples with control as a modifier and other keys, I've looked at examples on the net and I've even had a peak at the source code. Typing the xte-commands into the console works, so the problem must be with xbindkeys messing up some commands with the bindings, as you can see in the last example where one set of commands works and another fails with the same button combination. Bug?

(If this is in the wrong category, please move. It somehow belongs everywhere.)

---

