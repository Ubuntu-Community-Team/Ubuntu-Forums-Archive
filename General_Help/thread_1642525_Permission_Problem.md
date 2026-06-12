---
title: "Permission Problem"
date: 2010-12-10
forum: General Help
---

### Post by ValerieValirah on 2010-12-10
Let me start by saying that I've been using Ubuntu for a while but haven't had many problems and am not 100% sure on the terminology here.  I tried a google search to correct the problem and found other's with permission problems but didn't really understand how to modify the answer they were given to work for my particular problem and I didn't want to crew up my computer!

That out of the way, here goes:

I am using Ubuntu 10.10 on a Lenovo X100e

I downloaded software that runs on Java called Snowflake Pro.  I have been able to run the program by going through the file directory, right clicking and opening with java.

However, when I click on the program shortcut/ icon/ whateveritscalled in the applications drop down box (start menu?) I get the following:
[B]
Could not launch application[/B]
Failed to execute child process "/usr/local/Snowflake Pro 1.1.1/SnowPro" (Permission denied)

So I right clicked on the icon/ shortcut for the program and it had the following command line:

"/usr/local/Snowflake Pro 1.1.1/SnowPro"

I had been opening the program using Snowflake.jar 

So I switched the command line to 
"/usr/local/Snowflake Pro 1.1.1/Snowflake.jar"

And then got this error:
Failed to execute child process "/usr/local/Snowflake Pro 1.1.1/Snowflake.jar" (Permission denied)

So then I tried
"/usr/local/Snowflake Pro 1.1.1/Snowflake"   as a shot in the dark and got another "Could not launch application" error message.

How do I fix this problem so that the shortcut/ icon launches the program? (as going through the file directory is a bit tiresome.)

Thanks,
~Valerie

---

### Post by Morbius1 on 2010-12-10
And what happens when you use the full path:
```
java -jar "/usr/local/Snowflake Pro 1.1.1/SnowPro/Snowflake.jar"
```
I'm assuming that's the full path.

---

### Post by ValerieValirah on 2010-12-10
It works!!!!


Thank you so much!  I'd hug you, but this is the Internet...

---

