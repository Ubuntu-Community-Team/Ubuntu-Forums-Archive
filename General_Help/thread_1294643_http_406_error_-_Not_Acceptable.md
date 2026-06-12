---
title: "http 406 error - Not Acceptable"
date: 2009-10-18
forum: General Help
---

### Post by Bradosia on 2009-10-18
Here is the main scoop, My website ([asodar.com]("http://asodar.com")) gets a 406 error - Not Acceptable whenever I use a '%' in the url, such as asodar.com/?q=% and asodar.com/search/?q=%. Adding ?q=% after any directory seems to trigger this 406 error.

I have already searched many times to find a solution. I have tried disabling mod_security in my root .htaccess file with:

```
<IfModule mod_security.c>
SecFilterEngine Off
SecFilterScanPOST Off
</IfModule>
```

but still no luck fixing the problem. 
I have toyed around with it and this is what i found:
asodar.com/?q=% error
asodar.com/?q=%20 fine
asodar.com/?q=%25 error
asodar.com/?%=hi error
asodar.com/?q=40%ofmypie error

I have deleted my whole .htaccess file to see if anything in there caused the problem, though the problem still persists. Adding "?q=%" to the end of any directory on my server gets the error (even blank pages with no coding). While adding it to another website such as google.com gets no error. I have come to the conclusion that the problem lays in the settings of my server, but I have not changed any settings other than in the .htaccess file.

If anyone could assist me in the solution to this problem, it would be very helpful.

---

### Post by Bradosia on 2009-10-25
Problem solved, no need for help anymore,
the problem was indeed mod_security.

---

