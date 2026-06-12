---
title: "No key input delay in terminal mode!"
date: 2011-12-16
forum: General Help
---

### Post by ksprasad on 2011-12-16
Hi All,

I am having a strange problem with Ubuntu 11.10. In the terminal mode(Ctrl+Alt+F2), there isn't any delay between key inputs. So, most of the times even though I pressed a key only once, it will be printed twice or thrice. This is really annoying. To run a command, I have to type letter by letter carefully. However, this happens only in terminal mode.

Any ideas?

Specs: Dell Xps 14 laptop, Ubuntu 11.10 32-bit.

Regards,
ksprasad

---

### Post by matt_symes on 2011-12-17
Hi

Take a look at

```
man kbdrate
```

You can set the keyboard rate and delay there. It requires sudo privileges as it access /dev/port.

BTW: Does it only happen in a terminal ? Do you get the same issue in a console or using gedit ?

Kind regards

---

### Post by ksprasad on 2011-12-17
Hi,

Thanks for the reply.

> 
BTW: Does it only happen in a terminal ? Do you get the same issue in a console or using gedit ?
Yeah. It happens only in terminal. No issues when I am working with gui mode. I can use console, vi, gedit without any problem.

I checked kbdrate. 'sudo kbdrate' in console produced following output.

```

Typematic Rate set to 10.9 cps (delay = 250 ms)

```In terminal it produced slight different output.

```

Typematic Rate set to 11.0 cps (delay = 250 ms)
old delay 250, period 92
Typematic Rate set to 10.9 cps (delay = 250 ms)

```Still I haven't got why in terminal the rate is not getting set. Also I wonder why the output is different  in terminal even though I logged is using same userid :confused:
Also I tried to set some higher delay using -d option. But delay never occurred.

Regards,
ksprasad

---

### Post by matt_symes on 2011-12-17
Hi

I don't understand why it just happens to gnome terminal only.

Let's try to eliminate the X keyboard repeat all together

From a terminal

```
xset r off
```

Test in both gnome-terminal and gedit or libre-office (anything that uses X). Has the key repeat been switched off in gnome-terminal ?

To switch it back on

```
xset r on
```

Obviously, as this is an X setting, don't test in the console.

Post back results. 

Kind regards

---

### Post by ksprasad on 2011-12-18
> 
I don't understand why it just happens to gnome terminal only.


No! the gnome terminal and other gui part is proper. Sorry I was little confused with the terminologies - Console and terminal. As I mentioned in the first post, I am having problem with the black screen (Ctrl+Alt+f2) only. All the gnome part is fine.

Again sorry for the confusion.

Regards,
ksprasad

---

### Post by ksprasad on 2011-12-18
Hey.. The issue is solved now. I had to set the delay very high in console. If set it to 1000 ms. It is waiting for about 250 ms. This is strange but solved my problem :)

Thanks for your help.

Regards,
ksprasad

---

