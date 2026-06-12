---
title: "Possible race isue in init scripts"
date: 2010-01-13
forum: General Help
---

### Post by djm-uk on 2010-01-13
Not sure whether to post this as a bug or not - so will post here to be shot down!! Posting this as Ubuntu rather than Myth as it happens very early during startup...

I have a (myth)buntu 9.10 box using an intel atom 330 dual core board.  At random intervals the boot process would stop dead, usually just after 'setting preliminary keymap' but sometimes just before this point (after the root fs message). By dead I mean - no alt-f switch, no network connectivity, no disk activity, no c-a-d, no capslock response, no panic leds flashing.  Eventually decided it must be when X starts - tested by renaming /etc/init/gdm.conf & it seemed to work over a series of shutdown -r . Went round various X related tests - nomodeset, noacpi, irqpoll etc. Random means I cannot identify any trigger for it to happen or not - might not happen for a dozen then twice in a row, restart / power off / pull PSU makes no difference either way (AFAI Can tell)

As I had been caught by an LIRC race at a similar point on a hunch I put a 'sleep 5' in gdm.conf just before it starts gdm. it *SEEMS* to have fixed the issue (as I said it is random!).  Looking at the script it did occur to me that the gdm script issues the 'started' event BEFORE it actually starts gdm - so it is possible for another script to be reacting to this event before GDM has fully started & if GDM crashes out then the 'started' event has already been issued. If this is happening in other scripts then there is a potential for a race situation where a process is reacting to a 'started' event before the issuing process has actually fully started.  

Perhaps (in all scripts) the 'started' event should be issued AFTER the process has been started and returned to the init script - although if the process doesn't return to the script then that might be a problem...

David

---

