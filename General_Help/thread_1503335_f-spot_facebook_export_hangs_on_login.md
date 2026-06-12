---
title: "f-spot facebook export hangs on login"
date: 2010-06-06
forum: General Help
---

### Post by teddmeister2 on 2010-06-06
I have been trying to use f-spot to export pictures to facebook.  I looked around and saw some people's hanging on fetching albums or whatever.
My login hangs on "session established, fetching friend details", and eventually gives me the login button again, which I press to no avail.
I run f-spot --debug and get no error reports.

Can anyone help me with this?

---

### Post by teddmeister2 on 2010-06-07
Does anyone have any suggestions for how I can get this to work?

---

### Post by paxmanchris on 2010-09-05
I know you made this post way back in 2007, but I found it on a search..

I too am having the same problem,

I am able to establish a connection to facebook but it hangs on fetching photo albums..

[Debug 21:28:28.767] Authorizing Session
[Debug 21:28:29.085] Session established, fetching user info...
[Debug 21:28:29.338] Session established, fetching friend list...
[Debug 21:28:29.485] Session established, fetching friend details...
[Debug 21:28:29.663] Session established, fetching photo albums...



perhaps its just taking a long time to retrieve the data??

---

