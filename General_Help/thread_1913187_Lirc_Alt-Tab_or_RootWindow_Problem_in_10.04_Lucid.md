---
title: "Lirc Alt-Tab or RootWindow Problem in 10.04 Lucid"
date: 2012-01-22
forum: General Help
---

### Post by ult_avatar on 2012-01-22
Hi,

since I've upgraded recently from Kramic i ran into the following Problem:

I could not Alt-Tab with my remote-control anymore. Therefore i could not switch between windows - which is a hassle.

Previously under Karmic this was done with Lirc and irxevent:
```

begin
        prog = irxevent
        button = WindowsKey
        config = Key ALt-Tab RootWindow
end

begin
        prog = irxevent
        button = Enter
        config = Key Return RootWindow
end

```

Unfortunately this did not work anymore. All the other irxevents did work, however. I tried everything: different Key descriptions, different target windows (Current, ids, etc).

Finally I gave up and looked for other possibilities and found **xte**

```
begin
        prog = irexec
        button = WindowsKey
        config = xte 'keydown Alt_L' 'key Tab'
        end
begin

        prog = irexec
        button = MouseMenu
        config = xte 'keyup Alt_L'
        end

```

Now it works just as before in Karmic.

I hope this will be useful for someone else.


cheers
      ult_avatar

---

