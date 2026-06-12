---
title: "Firefox cannot open this URL"
date: 2009-08-29
forum: General Help
---

### Post by neon100 on 2009-08-29
i am using firefox 3.0.3 in hardy. But it is not opening this URL
[https://online.mcb.com.pk/ipc/](https://online.mcb.com.pk/ipc/)
apparently this page employs java which it is not supporting
any work arounds?

---

### Post by DeMus on 2009-08-29
> **neon100 said:**
> i am using firefox 3.0.3 in hardy. But it is not opening this URL
[https://online.mcb.com.pk/ipc/](https://online.mcb.com.pk/ipc/)
apparently this page employs java which it is not supporting
any work arounds?

Yes, it can. Look at the screenshot.

If it doesn't work for you, start Firefox in terminal and see what errors pop up.

---

### Post by warreno on 2009-08-29
> **neon100 said:**
> i am using firefox 3.0.3 in hardy. But it is not opening this URL
[https://online.mcb.com.pk/ipc/](https://online.mcb.com.pk/ipc/)
apparently this page employs java which it is not supporting
any work arounds?

Doesn't work in Firefox on Mac either, nor in Safari.

Tried it using Epiphany in my Ubuntu 9.04 in VirtualBox, and it doesn't work there either. I have Java enabled in all my browsers.

The fault isn't with Firefox; it's the web site.

---

### Post by neon100 on 2009-08-29
> **DeMus said:**
> Yes, it can. Look at the screenshot.

If it doesn't work for you, start Firefox in terminal and see what errors pop up.

How do i start firefox in terminal?

And problem is not with the website because it is opening easily on windows xp with firefox 3.5

---

### Post by DeMus on 2009-08-29
> **neon100 said:**
> How do i start firefox in terminal?

And problem is not with the website because it is opening easily on windows xp with firefox 3.5

Just open terminal ( Applications > Accessories > Terminal) and type firefox

---

### Post by warreno on 2009-08-29
> **neon100 said:**
> And problem is not with the website because it is opening easily on windows xp with firefox 3.5

I wonder if it's a language or character set support issue. My Mac, for instance, doesn't have a lot of non-English/Roman character support; neither does Jaunty as it runs here in VirtualBox.

Perhaps the reason it works for your Windows install and for **DeMus** is that you've got native support for something that I lack, only in her case she's got it in Ubuntu as well. If so, the trick will be to find out what language/character set you're missing in Ubuntu, and install it.

---

### Post by neon100 on 2009-08-29
> **DeMus said:**
> Just open terminal ( Applications > Accessories > Terminal) and type firefox

ERROR: "Unable to run application. Please enable java in browser"

---

### Post by DeMus on 2009-08-29
> **warreno said:**
> only in her case she's got it in Ubuntu as well.

The she you are referring to is in fact a he.

You could be on to something. I have no problem whatsoever to open the page. I run the English version of Ubuntu, with no other languages installed.
Does that to find the solution?

---

### Post by warreno on 2009-08-29
> **DeMus said:**
> The she you are referring to is in fact a he.

You could be on to something. I have no problem whatsoever to open the page. I run the English version of Ubuntu, with no other languages installed.
Does that to find the solution?

Sorry. I was going by your avatar, which looks rather feminine to me.

Thing is that I'm definitely using English only, so it's getting stranger and stranger that it works for you and not for me.

---

### Post by DeMus on 2009-08-29
> **warreno said:**
> Sorry. I was going by your avatar, which looks rather feminine to me.

Thing is that I'm definitely using English only, so it's getting stranger and stranger that it works for you and not for me.

It's okay. The avatar is my youngest daughter. Easy to make such a mistake.
Yes, that is strange since we both use the English version. What else could it be?

Btw, are you up early, or are you up late? I mean living in Arizona. Must be around 5 in the morning there.

---

### Post by neon100 on 2009-08-29
EXACTLY the same situation as warreno

So no solution. eh?

---

### Post by DeMus on 2009-08-29
> **neon100 said:**
> EXACTLY the same situation as warreno

So no solution. eh?

Did you try opening it in a terminal? What messages did you get?

---

### Post by warreno on 2009-08-29
> **DeMus said:**
> It's okay. The avatar is my youngest daughter. Easy to make such a mistake.
Yes, that is strange since we both use the English version. What else could it be?

Btw, are you up early, or are you up late? I mean living in Arizona. Must be around 5 in the morning there.

I'm up late, I guess, depending on perspective, but Arizona is -7 off GMT, so here it's just about 3 AM.

My Mac reports its Java version is 12.3.0. [java.com]("http://www.java.com/") reports that it can't get at my Java install, in either Mac or Ubuntu, so it believes there's a fault in the installation.

Aha. In Ubuntu, when I went to java.com and clicked the "Do I have Java" link, Firefox told me I had a missing plugin. Clicking the "Install" button got me the screenshot I've attached here. I selected the "Iced Tea" plugin but it's still downloading. (Slow DL; ETA is about 45 minutes!) **neon100**, this might be a lead to what's happening with your system.

On OSX, I really have no idea what might be the problem with my Java install. I don't seem to be lacking any updates.

---

### Post by warreno on 2009-08-29
> **DeMus said:**
> Did you try opening it in a terminal? What messages did you get?

Reported in post 7. Same basic error as Firefox in GUI, it seems.

What's weird, to me, is the abject fail. Usually if I'm missing a plugin or need a newer version, I'm provided with a link for updating, at least on Mac. This site just dies silently and presents me with a blank page.

---

### Post by warreno on 2009-08-29
Iced Tea didn't seem to help.

Oh hell. This was a little too contorted, and at the same time a little too obvious. Okay, go to Applications -> Add/Remove, and make sure to select the "All Available Applications" from the "Show" popup menu.

Type "java" into the search field.

Select the "Sun Java 6 Runtime" item.

Click "Apply Changes".

(See attached screenshot.)

Went through the install, and that fixed it.

(See other screenshot.)

Hope this helps for you.

---

### Post by DeMus on 2009-08-29
> **warreno said:**
> Iced Tea didn't seem to help.

Oh hell. This was a little too contorted, and at the same time a little too obvious. Okay, go to Applications -> Add/Remove, and make sure to select the "All Available Applications" from the "Show" popup menu.

Type "java" into the search field.

Select the "Sun Java 6 Runtime" item.

Click "Apply Changes".

(See attached screenshot.)

Went through the install, and that fixed it.

(See other screenshot.)

Hope this helps for you.


So, it was a Java problem after all? Well, I also looked at the Java download page and I to got a message I don't have the latest one installed, according to Synaptic I have a newer one then the webpage tells me so I just leave it as it is. It ain't broken, so I don't fix it.

Let's hope Ne0n100 also gets things working.

Where in Arizona do you live btw? I've been there couple of times. Great state.

---

### Post by neon100 on 2009-08-29
> **warreno said:**
> Iced Tea didn't seem to help.

Oh hell. This was a little too contorted, and at the same time a little too obvious. Okay, go to Applications -> Add/Remove, and make sure to select the "All Available Applications" from the "Show" popup menu.

Type "java" into the search field.

Select the "Sun Java 6 Runtime" item.

Click "Apply Changes".

(See attached screenshot.)

Went through the install, and that fixed it.

(See other screenshot.)

Hope this helps for you.


It is already installed. Same problem is persisting. And Demus, i mentioned the error when i open in terminal... error says java plugin missing in your browser.

---

### Post by DeMus on 2009-08-29
> **neon100 said:**
> It is already installed. Same problem is persisting. And Demus, i mentioned the error when i open in terminal... error says java plugin missing in your browser.

Sorry, must have missed that. Did you do what Warreno wrote in his last post? It helped him.

---

### Post by warreno on 2009-08-29
> **neon100 said:**
> It is already installed. Same problem is persisting.

Well, puüp. It might be worth trying to uninstall the Java extensions (just uncheck the box and click Apply), then installing them again.

You might have to do that in Synaptic. If you do, go for the complete uninstall option.

---

