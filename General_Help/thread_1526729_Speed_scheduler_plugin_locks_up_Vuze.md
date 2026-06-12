---
title: "Speed scheduler plugin locks up Vuze"
date: 2010-07-08
forum: General Help
---

### Post by PlugInPrius on 2010-07-08
I'm having a problem with Vuze locking up when I use the speed scheduler plugin. I never had this issue when I was using them in windows.

Here is whats happening. I have speed scheduler set to pause my seeds during the day. sometimes when it pauses a finished torrent the status of the torrent will be stuck on "stopping". When it does this my bandwidth up and down drop to 0 and I cannot download new torrents. I cannot removed the "stopping" torrent or even restart it. Vuze just kind of locks up. I have to kill the java process and restart Vuse before I can get it working again.

Does anyone know how to fix this issue? I'm running the latest version of Vuze and the speed scheduler plugin on Ubuntu 10.04.

---

### Post by PlugInPrius on 2010-08-15
I'm thinking it has something to do with the auto checking of the torrent when its finished and Speed Scheduler wanting to stop the torrent.

I have set Speed Scheduler to only check every 5 minutes and that seems to help since the checking of the finished torrent finishes in less than 5 minutes most of the time. I have see it still lock up and I'm guessing it just happens to be checking the torrent when Speed Scheduler is wanting to stop it.

Anyone have any ideas on how to fix this so I dont have a locked up Vuze missing new torrent downloads?

---

### Post by PlugInPrius on 2011-05-04
I think I found the problem.

I previously had my computer setup to copy the finished torrent to a new location on a septate drive. I told it to copy then delete instead of just move to prevent data loss.

Now I have it set up so that the torrent is downloading and moving on the same drive. Since its on the same drive I just told it to move it since moving on the same drive is instant.

So far I have downloaded many large torrents and they have all paused successfully.

---

