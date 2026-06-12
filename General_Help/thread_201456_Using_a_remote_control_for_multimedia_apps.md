---
title: "Using a remote control for multimedia apps"
date: 2006-06-21
forum: General Help
---

### Post by Nonno Bassotto on 2006-06-21
My laptop has a infrared port I never used. Only today I realized that maybe I could use it and a cheap remote control to (what else?) remotely control some multimedia apps, a quite useful feature when you're looking movies or listening music on your bed.
But I'm not sure this is feasible. It seems that lirc provides the basic daemons for this kind of things; I've searched the forums a bit but didn't understand how to make it work. Basically:
1) Is this feasible at all?
2) What kind of remote controls are supported?
3) What applications support this?
It's not something I can't live without, but it would be really nice. O:)

---

### Post by olsonar on 2006-06-21
take a look at the lirc homepage: [http://www.lirc.org/]("http://www.lirc.org/") :)

quick answers:
1) maybe
2) almost any, depends more on reciever than remote
3) i don't know for most. i do know gxine supports it, but the site makes it sound like it could potentially be used with anything

also, mythtv provides a nice interface to lots of multimedia features, you might want to take a look at it.

---

### Post by Nonno Bassotto on 2006-06-22
Thank you for your answer. You say it depends more on the receiver than on the remote. I had a look to lirc site and they give a lot of instructions on how to build your own receiver and so on. But I simply wanted to use the infrared port on my notebook. You know, one of those infrared ports that almost any notebook has. I can't provide more details, because I couldn't find any in the specs of my notebook. I was not able to find out on the lirc site if this ports can be used. Can anybody give any advice?

---

### Post by christhemonkey on 2006-06-22
For a list of supported remote controls:
[http://lirc.sourceforge.net/remotes/](http://lirc.sourceforge.net/remotes/)

On the side of the page it says:
> Supported Hardware...
Commercially available:...

Built-in IrDA ports (SIR mode, available in notebooks)

So hopefully with any luck it should work!
Quite tempted to try an get IR remote control on my laptop now...

---

### Post by Nonno Bassotto on 2006-06-22
I've been trying to understand how to make it work, but it seems a hell. It seems I have to recompile a lot of things, but I'd rather try to avoid this if possible. It seems that some modules for my infrared port are already loaded, as lsmod|grep ir reports
```

via_ircc               32660  0
irda                  217980  1 via_ircc
crc_ccitt               2496  1 irda

```
Is there a way to make lirc use these drivers?
I've tried "sudo dpkg --reconfigure lirc" as  it should present me a list of hardware to choose from, but it doesn't.
I've also activated irw, but no output is shown when I press buttons on the remote control.

---

### Post by Nonno Bassotto on 2006-06-22
Actually my infrared port was disabled in the bios :oops: 
Now it is enabled and lsmod | grep ir shows
```

nsc_ircc               26256  0
via_ircc               32660  0
irda                  217980  2 nsc_ircc,via_ircc
crc_ccitt               2496  1 irda

```
I've tried
```

sudo irattach nsc_ircc

```
but irw still doens't show anything :(

---

