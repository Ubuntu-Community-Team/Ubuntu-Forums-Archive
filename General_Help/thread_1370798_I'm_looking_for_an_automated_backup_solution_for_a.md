---
title: "I'm looking for an automated backup solution for a computer that isn't always on."
date: 2010-01-02
forum: General Help
---

### Post by AKADAP on 2010-01-02
My computer is my desktop, and it runs the MythTV back end. I have it set up so that it will automatically turn on when MythTV needs to record a program, or alternatively, I can manually turn it on, log in and use it without interfering with the MythTV back ends recordings.

To do this, MythTV monitors when someone is logged in to the computer, and automatically shuts off the computer if it has nothing to record and no one is logged in.

I'd like to set up an automated backup for my files on this computer. I'd like it to do full backups at regular intervals, and incremental backups daily. I'd like it to do these backups late at night so they do not interfere with my use of the computer, or with MythTV recordings. I'd like it to do backups only when I have logged in since the last backup. If I have not logged in, there is no possibility of changes to any of the files I want backed up (I don't wish to backup MythTV recordings).

The problem lies in the fact that the powering on or off of my computer is handled by the MythTV back end. cron does not have this capability, though I think that is where this functionality should lie. Also, I am not aware of any backup software that works this way.

I am thinking that it may be possible to implement what I want with scripts within MythTV, but that is more of a hack than a generalized solution. I'd like to set this up on my fathers computer as well, but he does not run MythTV, so I would not be able to use a MythTV hack to get this to work on his computer.

I think in the long run, cron will need to be modified to control the powering on or off of the computer, but this is currently beyond my abilities. It will not be a trivial task, as it will have to check for users logged in to prevent shutting down on a user, and it will have to know which tasks should be allowed to run to completion, and which it can shut the system down on without consequences.

Does anyone have a better idea? No, leaving the computer on all the time is not an option. Certain people can not deal with LEDs on at night, or computers on when no one is using them.

---

