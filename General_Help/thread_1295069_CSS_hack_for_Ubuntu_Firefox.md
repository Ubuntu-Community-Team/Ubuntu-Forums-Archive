---
title: "CSS hack for Ubuntu Firefox?"
date: 2009-10-19
forum: General Help
---

### Post by ashwani007 on 2009-10-19
Hello Guys,

Is there any CSS hack available for Ubuntu Firefox???
Please let me know if there is, I need that urgently.

Thanks in advance,

Regards,
Ashwani Sharma

---

### Post by lovinglinux on 2009-10-19
I don't know exactly what you mean, but there [Stylish](https://addons.mozilla.org/en-US/firefox/addon/2108) extension, which allows you to modify CSS of web pages and the browser interface.

---

### Post by ashwani007 on 2009-10-19
@lovinglinux

Thanks for your support.
Actually I need CSS hack for Ubuntu Firefox. I've made a navigation tab area using windows default font 'Arial'. This is working fine in all browsers of Windows, but in Ubuntu Firefox its showing more letter spacing than Windows. That is creating spacing problem for my tabs. So I just need a CSS hack which will work over Ubuntu Firefox only.

---

### Post by lovinglinux on 2009-10-19
Perhaps you could ask a moderator to move this thread to the [Programming Talk](http://ubuntuforums.org/forumdisplay.php?f=39) sub-forum. Just click the report button on the left sidebar next to your first post. I think you will get better support for web development there.

---

### Post by falkenberg_cph on 2009-10-19
So Firefox in Windows is looking fine as well?

---

### Post by ashwani007 on 2009-10-19
Thank you all for your support
I got the solution for what i was looking :)
But we can use this using .asp code.
here is the solution:


<%
dim remoteOs , osName,osVal 
remoteOs= request.ServerVariables("HTTP_USER_AGENT")

osName =Split(remoteOs,";")
osVal=Split(trim(osName(2))," ")
'response.Write osVal(0)

if(osVal(0)="Windows")Then
    response.Write("<link href='css/main-windows.css' rel='stylesheet' type='text/css' />")
elseif (osVal(0)="Linux") then 
    response.Write("<link href='css/main-linus.css' rel='stylesheet' type='text/css' />")
else
    response.Write("<link href='css/main-mac.css' rel='stylesheet' type='text/css' />")
end if
%>

---

