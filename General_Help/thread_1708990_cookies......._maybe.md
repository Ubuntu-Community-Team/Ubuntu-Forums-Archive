---
title: "cookies....... maybe?"
date: 2011-03-17
forum: General Help
---

### Post by nothingspecial on 2011-03-17
I am doing an open university course.

They have a flash application that calculates your carbon footprint and saves your changes for the next time you open it. It uses your web browser.

I'm guessing this is a cookie.

How would I find out where firefox or midori saves this information so that I can use it on different computers? ie any changes I make one one computer can be transfered to another. I would rather not sync my browsers entire settings.

thanks

---

### Post by pqwoerituytrueiwoq on 2011-03-17
make the flash send the data to the server and store it and access wiht user name /password

why use flash for that just use a little JavaScript and html client side
maybe some css to make it look pretty

---

### Post by nothingspecial on 2011-03-17
> **pqwoerituytrueiwoq said:**
> make the flash send the data to the server and store it and access wiht user name /password

why use flash for that just use a little JavaScript and html client side
maybe some css to make it look pretty

I don't mind opening it with whatever.

I know nothing of how these things work. I have a folder that contains

```
AC_RunActiveContent.js  fulldata.xml  fullfootprint8.html  fullfootprint8.swf
```

I open the .swf file with midori and it gives me this fancy thing I can enter data into. I can change that data and next time I open it the data is saved.

I don't care what I run it with.

The point is, I would like to be able to use the data I have modified on one computer with another one. I can't find where these changes are stored.

So, what do I save and how do I save it on "the server". This method is ideal btw because all my boxes have access to my server.

Please assume I know nothing of html, java, css or anything else of that nature.

Thanks

---

### Post by nothingspecial on 2011-03-17
Alternatively, I can use (for example) a .screenrc saved on my server, locally  from any machine using the -c flag to load a saved config.

What I would like to do have an alternative config file/directory for a browser that I can use when I open the browser, that I can use exclusively with this application.

I'm not explaining myself very well.

When I change it on one box I want to be able to open the changed app on the other machine........

Think dropbox or ubuntuone

when it changes on one computer I would like it to change on the other one.

.......if you see what I mean.

---

### Post by pqwoerituytrueiwoq on 2011-03-18
can your post your formula?
as well as a screen shot of the flash object in the browser
*plans to remove flash as a dependency of this page*

---

### Post by FlashHater on 2011-03-18
I'd guess that since it's a flash application it would save in your "/home/.macromedia" folder. If that's the case all you'd need to do is copy it over to the other machine.

---

### Post by nothingspecial on 2011-03-18
> **FlashHater said:**
> I'd guess that since it's a flash application it would save in your "/home/.macromedia" folder. If that's the case all you'd need to do is copy it over to the other machine.

Bingo! 

Cheers :D

I put the .macromedia directory in my dropbox and symlinked it to the home directories of both machines.

---

