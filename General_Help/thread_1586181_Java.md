---
title: "Java"
date: 2010-10-01
forum: General Help
---

### Post by borth92 on 2010-10-01
This is not a problem, but me asking help programming something in Java.

I am taking a seconds integer and converting it into a "days:hours;minutes:seconds" format. But at the end it says "error: expected ')' "  Feel free to move this into the proper place in the forums...i wasnt sure where it belonged

this is what I have so far:

import java.util.*;
public class secToDay {
    public static void main (String[ ] args) {
        int seconds, days, hours, mins, secs;
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Please type seconds");
        seconds = scanner.nextInt( );
        
        days = seconds/86400;
        hours = (seconds/3600)-(days*24);
        mins = seconds/60-days*24*60-hours*60;
        secs = seconds-days*24*3600-hours*3600-mins*60;

        System.out.println(days":"hours":"minutes":"seconds);
        
    }
}

---

### Post by borth92 on 2010-10-01
and i just copied and pasted so ignore the things like the space between sec and s in secs. It all compiled well until the last System.out.println( command

---

### Post by lykeion on 2010-10-01
[PHP]System.out.println(days + ":" + hours + ":" + minutes + ":" + secs);[/PHP]

---

