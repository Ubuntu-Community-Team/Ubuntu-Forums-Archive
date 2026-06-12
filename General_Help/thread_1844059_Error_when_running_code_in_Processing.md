---
title: "Error when running code in Processing"
date: 2011-09-14
forum: General Help
---

### Post by DimitrisC on 2011-09-14
I came across a great arduino project to add ambilight to my pc monitor when playing movies.

The author of the project posted detailed instructions on how to make it work and was kind enough to provide us with his code.

[http://siliconrepublic.blogspot.com/2011/02/arduino-based-pc-ambient-lighting.html](http://siliconrepublic.blogspot.com/2011/02/arduino-based-pc-ambient-lighting.html)

I downloaded processing both on my windows desktop and on my linux laptop to give the code a try and see how it works. 
When I paste the code from the website into processing under windows it runs fine as expected.

When I paste the same code in processing under linux it throws errors. The processing application starts fine under ubuntu but gives an error when running the exact same code that seems to be working just fine in windows!!!

Am I missing something? Shouldn't it work the same under both operating system since it is in processing under both? 

Thanks!

---

### Post by DimitrisC on 2011-09-16
Bump!

This is the error I am getting in processing:

Exception in thread "Animation Thread" java.lang.ArrayIndexOutOfBoundsException: 0
	at ColorPicker.setup(ColorPicker.java:43)
	at processing.core.PApplet.handleDraw(Unknown Source)
	at processing.core.PApplet.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)

Can someone help please? I really would like to test this project and I only have a linux laptop!

---

