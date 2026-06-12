---
title: "How do you kill a java program?"
date: 2010-08-08
forum: General Help
---

### Post by Cyborg31 on 2010-08-08
Besides finding out the process ID and typing kill ID?

Ctrl+C doesn't work.  If I start my java program (which runs in a loop), Ctrl+C only types ^C and doesn't do anything.  I have to open up another terminal, log in, find the ID, and kill it.

Thanks.

---

### Post by dino99 on 2010-08-08
use system-monitor and select your app into process to kill it

you may consider this java app as:

- very buggy, so you might forget it
- or badly installed, in that case: remove/purge it with synaptic then reinstall it

you might find usefull errors logged too (system admin logviewer, .xsession-errors)

---

### Post by Cyborg31 on 2010-08-08
Oh, is there no other way via keyboard command? I'm SSHing into a remote ubuntu server with PuTTY.  It's the same using a linux terminal.

I'm not sure if it's the java program's fault.  Even a simple program like this doesn't let me Ctrl+C.
```

import java.util.*;
import java.io.*;
public class Hello
{
    public static void main(String[] args) 
    {
        System.out.println("Enter your name: ");
        Scanner scan = new Scanner(System.in);
        String line = scan.nextLine();
        System.out.println("Hello " + line);
    }
}
```

---

### Post by X.Cyclop on 2010-08-08
**Type Ctrl+Z (and then ps or jobs... > jobs > kill %PROCESS ID)**, this way, at least, you don't have to open a new terminal.

---

### Post by timvoet on 2010-08-09
the reason CTRL-C doesn't end that simple program, the program is waiting for user input, and CTRL-C is valid input.

---

### Post by elricscripts on 2010-08-10
You could add "force application to quit" to your panel.

---

