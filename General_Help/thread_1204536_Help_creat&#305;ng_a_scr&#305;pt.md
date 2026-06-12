---
title: "Help creat&#305;ng a scr&#305;pt"
date: 2009-07-04
forum: General Help
---

### Post by R2D2! on 2009-07-04
I'm try&#305;ng to create a scr&#305;pt for wm&#305;nput that uses not&#305;f&#305;cat&#305;ons.

I have the follow&#305;ng:
```
ilhui@laptop:~$ sudo wminput
[sudo] password for ilhuitemoc: 
Put Wiimote in discoverable mode now (press 1+2)...
No Bluetooth interface found
unable to connect

```

That &#305;s supposed to happen, s&#305;nce I have no bluetooth connected. But when I try someth&#305;ng l&#305;ke
```
notify-send Wminput "$(sudo wminput)"
```
only the 1st l&#305;ne goes to notify-send, and the following 2 go to the term&#305;nal.

Is there someth&#305;ng I can do to send the whole message to notify-send?

—Ilhu&#305;temoc

P.S. Yes, I'm a noob :p

---

### Post by Brandon Williams on 2009-07-05
I expect that the first line is being sent to stdout and the next two lines are being sent to stderr. Only stdout is captured by $(...). Try this: "$(sudo wminput 2>&1)"

---

### Post by R2D2! on 2009-07-05
It sends &#305;t &#305;n the wrong order:

No Bluetooth interface found
unable to connect
Put Wiimote in discoverable mode now (press 1+2)...

And &#305;f &#305;t's a successful connect&#305;on, &#305;t doesn't send anyth&#305;ng, so &#305;t becomes useless...

&#8212;Ilhu&#305;temoc

P.S. I don't know if there's something to make the commands like
```
notify-send Wminput "Put Wiimote in discoverable mode now"
notify-send Wminput "No Bluetooth interface found"
notify-send Wminput "unable to connect"
```

---

