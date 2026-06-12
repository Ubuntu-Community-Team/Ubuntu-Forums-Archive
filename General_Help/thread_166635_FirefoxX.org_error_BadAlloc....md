---
title: "Firefox/X.org error: BadAlloc... ????"
date: 2006-04-26
forum: General Help
---

### Post by conro on 2006-04-26
I somehow managed to break firefox, but i'm not exactly sure how i did it.
Everything was working fine, and i started messing with the alpha settings in fluxbox. I made all of my menus transparent, then i started firefox and it would show up for a split second and then close. 
```

The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2480 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
conor@skank:~$ 

```
i tried running firefox with the --sync flag that it mentions and i get the same error. i reset the alpha levels in FB and the error still occurs, and i can't think of anything else that i did that could have messed things up. 

Currently i am using opera, and it works ok, but it gives the following errors in the console which seem like they could be related... 
```

motifwrapper: X Error: BadWindow (invalid Window parameter)
motifwrapper: X Error: serial=0x1164, request=0x4, request_minor=0x0, resource=0

```

it seems like it would be a windows manager issue, but i am new to ubuntu, and i am not really sure how to reinstall a program through apt. 

anyone have any ideas or suggestions? 
thanks!

---

