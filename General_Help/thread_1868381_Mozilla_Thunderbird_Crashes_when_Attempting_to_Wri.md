---
title: "Mozilla Thunderbird Crashes when Attempting to Write New Email"
date: 2011-10-24
forum: General Help
---

### Post by Faylcon on 2011-10-24
I am running Ubuntu 11.10 and up until two days ago, Thunderbird worked fine. Now, whenever I click on the "Write" button, Thunderbird freezes and the screen grays out. I opened Evolution and was able to send an email with no problem.

---

### Post by Joeb454 on 2011-10-24
Can you try running the following command from a termianl
```
thunderbird > ~/Desktop/thunderbird.txt
```

This will run thunderbird and put any output into a 'thunderbird.txt' file on your desktop. If you replicate the issue, can you then upload that file so we can see what thunderbird's trying to do?

---

### Post by zreivaj9 on 2011-10-25
> **Joeb454 said:**
> Can you try running the following command from a termianl
```
thunderbird > ~/Desktop/thunderbird.txt
```This will run thunderbird and put any output into a 'thunderbird.txt' file on your desktop. If you replicate the issue, can you then upload that file so we can see what thunderbird's trying to do?

I have the same problem when replying messages.h
Here you have my output. It seems a problem with some calendar that is unavailable for some reason.
------------------------------------------
(thunderbird-bin:5332): GLib-GObject-WARNING **: cannot register existing type `DbusmenuServer'

(thunderbird-bin:5332): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(thunderbird-bin:5332): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
Warning: There has been an error reading data for calendar: Trabajo.  However, this error is believed to be minor, so the program will attempt to continue. Error code: 0x80004005. Description: A request Error Occurred. Status Code: 500 Internal Server Error Body: <html><head><meta http-equiv="content-type" content="text/html;charset=UTF-8">
<title>Error</title>
<style type="text/css">body {font-family: arial,sans-serif}</style></head>
<body text="#000000" bgcolor="#ffffff"><table border="0" cellpadding="2" cellspacing="0" width="100%"><tr><td rowspan="3" width="1%" nowrap><b><font face="times" size="10"><font color="#0039b6">G</font> <font color="#c41200">o</font> <font color="#f3c518">o</font> <font color="#0039b6">g</font> <font color="#30a72f">l</font> <font color="#c41200">e</font></font>&nbsp;&nbsp;</b></td>
<td>&nbsp;</td></tr>
<tr><td bgcolor="#3366cc"><font face="arial,sans-serif" color="#ffffff"><b>Error</b></font></td></tr>
<tr><td>&nbsp;</td></tr></table>
<blockquote>No se puede acceder al calendario que has solicitado.</blockquote>
<p></p>
<div style="background:#3366cc; width:1px; height:4px"></div></body></html>
Warning: There has been an error reading data for calendar: Trabajo.  However, this error is believed to be minor, so the program will attempt to continue. Error code: READ_FAILED. Description: 
------------------------------------------------------

Regards,
ZReivaj.

---

### Post by Faylcon on 2011-10-26
UPDATE: Here's the thing the thunderbird > ~/Desktop/thunderbird.txt command produces an empty .txt file. However, if I run sudo Thunderbird, I can write new emails with no problem. Any ideas why this would have changed in the last few days?

---

### Post by Faylcon on 2011-10-28
UPDATE: After the latest round of program updates, Thunderbird is operating normally again.

---

