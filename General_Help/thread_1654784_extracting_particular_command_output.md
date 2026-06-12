---
title: "extracting particular command output"
date: 2010-12-28
forum: General Help
---

### Post by MichaelBurns on 2010-12-28
I want to know the best way to extract a particular part of a command's output.  Some commands apparently come specially equipped for this purpose, and allow one to specify only the part of the output that they want.  However, sometimes the documentation at least is lacking any indication of this.  For example, I want to get the window id of the root window.  The **xwininfo** command will give this to me:
```

user@computer:~$ xwininfo -root

xwininfo: Window id: 0x92 (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
:
:
:

```
Then I want to extract the id number using **awk**.  This is where I get stumped.  I want to write the command genericly so that the format of the output doesn't matter, so long as the id number always follows "Window id:".  So, there are two ways that I think that this might be done (but I haven't yet figured out the syntax for either).  One way would be to loop through the **awk** fields until one of them matches "Window" and the next one matches "id:", and then print the next field:
```

user@computer:~$ xwininfo -root | awk '$N ~ /Window/ AND ${N+1} ~ /id:/ { print ${N+2} }'

```
(Obviously I'm no **awk** expert; consider the above as pseudocode.)  The other way would be to just match to the literal regex "Window id:" and then print whatever follows the following space, but I don't know how to use regex to do this:
```

user@computer:~$ xwininfo -root | awk '/Window id:/ { print IDNUM }'

```
where I want the regex to extract the IDNUM by matching (-) the "Window id:" string, then starting (>) at the next space, and then stopping (<) at the next space:
```

xwininfo: Window id: 0x92 (the root window) (has no name)
          ---------->    <

```
Does anyone know syntax for either of these two approaches, or have an alternative suggestion?

---

### Post by hawkmage on 2010-12-28
It may not be elegant but this is what I cam up with using grep and sed:
```
xwininfo -root | grep 'Window id:'  | sed 's/^.*Window id: \(0x[[:xdigit:]]\+\) .*/\1/'
```

---

### Post by MichaelBurns on 2010-12-29
Thanks, hawkmage.  That may be what I'm looking for.  Like you said, though, it may not be elegant.  In fact, I think that the regex part of the grep manpage warns against using backreferences.  Of course, if it works ...  I just like to try to be as portable/durable as possible.

---

### Post by hawkmage on 2010-12-29
Luckily the grep portion of the command is not using back references.  All grep is doing is pulling the line that contains the "Window id:" text.  The sed command is the one using the back reference.  If you are familiar with the substitute command in vi the substitute in sed is the same.  Depending on the regex engine that sed is using you may need to change the ```
[[:xdigit:]] to [0-9a-fA-F]
```It all depends on if the version of sed supports POSIX regex character classes or not.

---

