---
title: "espeak meltdown"
date: 2009-11-21
forum: General Help
---

### Post by cntrygrl17 on 2009-11-21
I wanted to show my mom how the espeak works in the terminal, but when I typed in "espeak hello" is gave me this:
 bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

and I really just have no idea how to fix it! plz help?!

---

### Post by Scipio_Publius on 2009-11-25
I got the same thing but I type 

```
scipio@IMP:~$ espeak
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Hello Mom

```

And is says what I type on the screen.

```
espeak -f file.txt 
```

works too

sorry I didn't help explain the messages but I just experimented a little and it worked.  Do you hear no sound at all?

---

