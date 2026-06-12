---
title: "java version conflict"
date: 2006-06-09
forum: General Help
---

### Post by weissnich on 2006-06-09
Hi,

I installed sun-java from the multiverse repository. 
But when I type java-version it shows 
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

```
This gij is installed with openoffice.org, what can I do?

Thanks!

---

### Post by Bokonon on 2006-06-09
If you want to switch the java location, you can do

```
sudo update-alternatives --config java
```

Then select the sun package which is installed in /usr/lib/jvm/ I believe.
I did the same for jar, javac, and javaws, but that may be a waste if you can get rid of the extra packages you don't want/need.

Right now, I just have one version installed.  I got rid of the gij/gcj type java packages on my last reinstall and haven't missed them much.  Poke around here and you should be able to get rid of most/all of that stuff.

---

### Post by donmiguel on 2006-11-01
i did exactly what Bokonon proposed to do.

and it worked! when i check:

```

% java -version

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)


```

SO i tried to compile a little program from core Java with Java5.0 syntax:

```

/**
Welcome.java
on 1.20 2004-02-28
   @author Cay Horstmann
*/
public class Welcome
{
   public static void main(String[] args)
   {
      String[] greeting = new String[3];
      greeting[0] = "Welcome to Core Java";
      greeting[1] = "by Cay Horstmann";
      greeting[2] = "and Gary Cornell";
      for (String g : greeting) System.out.println(g);
   }
}

```

what i get from compiling this beautiful little greeting program:

```

% javac Welcome.java

----------
1. ERROR in Welcome.java (at line 13)
        for (String g : greeting) System.out.println(g);
             ^^^^^^^^^^^^^^^^^^^
Syntax error, 'for each' statements are only available if source level is 5.0
----------
1 problem (1 error)
```

Why? i mean Whyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy? :)
in fact the sharing VM thingy is making me a little suspicious but i have no idea what to think of it.. 

i'd be very glad if sb could give me a hint or so
thanks a lot already

donmiguel

---

