---
title: "devilspie help"
date: 2006-06-04
forum: General Help
---

### Post by _simon_ on 2006-06-04
I'm trying to get it so that swiftfox starts centered.

My script file is simply as follows:

```

(if
    (matches (application_name) "firefox-bin")
    (begin
       (center)
        
       
    )
)

```

This seems to do nothing. 

I have also tried:

```

(if 
  (is (application_name) "firefox-bin") 
  (center)
)

```

If I run ```
devilspie -d
``` I get:

```

simon@ubuntu:~$ devilspie -d
Devil's Pie 0.16 starting...
Loading /etc/devilspie
/etc/devilspie doesn't exist
Loading /home/simon/.devilspie
Loading /home/simon/.devilspie/swiftfox.ds

```

I assume it's not supposed to hang on "Loading"?

If I try loading the file directly I get:

```

simon@ubuntu:~$ devilspie /home/simon/.devilspie/swiftfox.ds -d
Devil's Pie 0.16 starting...
Loading /home/simon/.devilspie/swiftfox.ds

```

---

### Post by enric on 2006-06-06
[QUOTE=_simon_]
I assume it's not supposed to hang on "Loading"?
[/QUOTE]

Yes it is.

The program devilspie must be running at the moment you load firefox.  You can leave it in the background or run it automatically at the start of your session with gnome-session-properties.

---

### Post by _simon_ on 2006-06-06
I'd forgotten I posted this!

Thank you for the reply - I got it working correctly a few days ago :)

---

### Post by TLE on 2006-06-17
Could you please write what the problem was and how you fixed it. I can't get it working either

---

### Post by jinacio on 2006-06-23
you shoud backround devilspie (note the '&'):
```
devilspie -d &
```

if it doesn't match application_name, try:
```
(contains (window_name) "Firefox")
```

---

### Post by _simon_ on 2006-06-23
[http://www.ubuntuforums.org/showthread.php?t=188948&highlight=devilspie](http://www.ubuntuforums.org/showthread.php?t=188948&highlight=devilspie)

---

