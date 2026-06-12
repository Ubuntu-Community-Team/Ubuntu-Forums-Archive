---
title: "Freepascal 2.0.2 IDE + Ubuntu Dapper problem"
date: 2006-06-26
forum: General Help
---

### Post by lofiye on 2006-06-26
Hi!

I use Ubuntu on both my desktop and my laptop, and i've troubles running the freepascal (2.0.2) IDE on both machines.

When i use a 'real' console (switching with ctrl_alt_f2 for ex.) and try to execute 'fp', no IDE appears, and the 'fp' proces (checked with top) takes 100% cpu time. I have to quit the proces using ctrl-z.

On my laptop, exactly the same happens. The compiler (fpc) itself works just fine on both machines. I also tried to compile fpc 2.0.2 from source, but that didn't resolve the issue. 

The weird thing is that i actually can run the IDE on both systems when i use a gnome terminal... 

Anyone knows what's going on here?

I also have a server running Gentoo Linux, and it runs the IDE without any trouble at all..

I have gotten a development version of the IDE working (i believe 2.1.x) , but that introduced some other (probally non ubuntu) bugs. I really would like to stick with 2.0.2 for now...

I hope someone can help me out here :)

Best regards,

Dennis

---

### Post by lofiye on 2006-06-29
No FPC/Ubuntu users out there?  :D

---

### Post by lofiye on 2006-07-07
I fail to understand why it isn't working. I'am running vector linux at the moment on which fpc works just fine. I will try ubuntu again in the future. It's awesome in most respects, but i need fpc right now.

I'am still interested to know if there people out there actually running (console) fpc on dapper.

Thanks.

Dennis

---

### Post by HansGong on 2006-07-07
I've installed fp on Dapper successful.I recommend you to reinstall it.Actually,fp in mono is not a better enviroment for programing.I think anjuta+fp compiler is better.

---

### Post by lofiye on 2006-07-07
Hi!

Thank you for replying! Why do you mean with 'mono'? Anjuta could be an option, but i really would like to stay out of X while programming :D 

Does the included fp IDE work for you from a -real- console? 

Thanks!

Dennis

---

### Post by HansGong on 2006-07-07
Fp in a real control looks quite ugly.And the functions such as "writeln" or "write" works out of the way.

---

### Post by lofiye on 2006-07-14
I don't understand what you are trying to say about fp. I'am currently running xubuntu, and the fp gui is still not working from a real console. 

Suggestions are welcome as ever...

Dennis

---

### Post by thingy on 2006-07-14
According to this link, the text mode ide has problems working on unix systems.

[http://www.freepascal.org/faq.html#ideinst](http://www.freepascal.org/faq.html#ideinst)

Can you try the typing in fp -F

[http://www.freepascal.org/docs-html/user/usersu26.html#x53-590006.1.2](http://www.freepascal.org/docs-html/user/usersu26.html#x53-590006.1.2)

jin

---

### Post by lofiye on 2006-07-17
fp -F doesn't solve the problem. I'am not sure how relevant the faq entry really is at this moment. They seem to be talking about an old version of fpc.

---

