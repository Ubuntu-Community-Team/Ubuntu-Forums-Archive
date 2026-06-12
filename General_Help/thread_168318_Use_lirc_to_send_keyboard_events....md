---
title: "Use lirc to send keyboard events..."
date: 2006-04-30
forum: General Help
---

### Post by encompass on 2006-04-30
I want to set up my computer to do presentations... I have lirc working perfectly... but I don't know what I could do to send keyboard events to the computers current window.
I figure it could be done with irexec.
You know...> irexec <down-arrow>
It would be nice to have that working as I am setting this computwr up to demo ubuntu in front of 200 plus people.  Ideas?:-D

---

### Post by encompass on 2006-05-04
found it... pretty darn simple...
I used this in my .lircrc file...
> begin
        prog = irxevent
        button = BLUE
        config = Key Right CurrentWindow
end

begin
        prog = irxevent
        button = RED
        config = Key Left CurrentWindow
end

irxevent is the program.
I use it to run my Presentations now and it works wonders.
Hope this helps someone else out there.

NOTE... I also turn on irxevent too... :P

---

