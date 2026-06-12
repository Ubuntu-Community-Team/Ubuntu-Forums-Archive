---
title: "Java doesn't work"
date: 2006-02-06
forum: General Help
---

### Post by feathers on 2006-02-06
Whatever I do, I always get this message in my simple "hello world" programme: 
Exception in thread "main" java.lang.NoClassDefFoundError: Main/class

My sourcecode: 

```
class Main
{
        public static void main (String[] args)
        {
        System.out.println( "Hello, world!" );
        }
}
```
This is the command to start it: java Main.class
I installed various jre's and sdk's and set them with update-alternatives. The funny thing is, it works in Eclipse, I mean I can start the class in Eclipse but I cannot do this on the console. This is the case with several kubuntu computers I have checked. 
Who can help? Thanks!

---

### Post by nrwilk on 2006-02-06
I can't help you with the problem, but I wanted to let you know that there is a code development forum lower down on the main forum index page.

Maybe you'll have a better response there?

I hope you find your problem!

---

### Post by feathers on 2006-02-07
Problem solved. You start a java programme without the .class.

---

