---
title: "Java won't run outside Eclipse - ClassNotFound"
date: 2009-10-02
forum: General Help
---

### Post by mazz0 on 2009-10-02
Is there some complicated terminal based annoyance I need to go through to get Java working from the terminal?  When I run my programme within Eclipse it runs fine, but when I run it from the terminal it says this:

```
Go: ls
RegExTest.class
Go: java RegExTest.class
Exception in thread "main" java.lang.NoClassDefFoundError: RegExTest/class
Caused by: java.lang.ClassNotFoundException: RegExTest.class
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: RegExTest.class.  Program will exit.
Go: 

```What do you mean ClassNotFound?  IT'S RIGHT THERE!!!!!

I'm sure there is insufficient information here to resolve my problem, but I don't really know what info to give.  I've got the Sun Java 6 JDK.  Any other info people think might be helpful?

Here's the source code of the example (RegExTest.java) I'm using, so you can comfirm it works for you, although I have the same problem with any programme.  I would have attached this file, but for some reason my attachment page keeps timing out.

```
import java.util.regex.Matcher;
import java.util.regex.Pattern;

public class RegExTest
{
    public static void main(String args[]) throws Exception
    {
        //Regular Expression goes here
        String regEx = ".";
        //String to match against goes here
        String stringToMatch = "abc123";
        
        //Run test
        printMatches(regEx, stringToMatch);
    }
    
    public static void printMatches(String myRegEx, String myStringToMatch)
    {
        //print out what we're about to do
        System.out.println("RegEx:\t\t" + myRegEx);
        System.out.println("String:\t\t" + myStringToMatch);
        System.out.println("");
        
        try
        {
            //create the regex
            Pattern myPattern = Pattern.compile(myRegEx);
            Matcher myMatcher = myPattern.matcher(myStringToMatch);
            
            //keep running the regex and if there's a match print it out (and keep a count)
            int matchesCount = 0;
            while(myMatcher.find())
            {
                System.out.println("Match " + (matchesCount + 1) + ":\t" + myMatcher.group());
                matchesCount++;
            }
            
            //print the count of matches found
            System.out.println("");
            if(matchesCount == 1)
                System.out.println("One match");
            else
                System.out.println(matchesCount + " matches");
        }
        catch(Exception e) //print out what's wrong with the regex
        {
            System.out.println(":( Looks like the Regex is wrong:");
            System.out.println("");
            System.out.println(e);
        }
    }
}
```

---

### Post by Mighty_Joe on 2009-10-02
Java uses an environment variable called CLASSPATH to find class files. Have a look at [this article]("http://faq.javaranch.com/java/HowToSetTheClasspath") for how to work with it.

---

### Post by mazz0 on 2009-10-02
The only imports are part of the Java package, I shouldn't need to specify anything else in the classpath should I?

---

### Post by Mighty_Joe on 2009-10-02
Java knows where to find the java.* classes. They're part of the API. You have to tell Java where to find *your *class.

Ah, I see a problem.  Look at this:
```

Go: java RegExTest.class
Exception in thread "main" java.lang.NoClassDefFoundError: RegExTest/class

```
You are supposed to pass the class name to Java, not the class *file *name.  Try just: 
```

java RegExTest

```

---

### Post by mazz0 on 2009-10-02
```
me.isStupid() == true
you.isAce() == true
```

Thank you very much :)

---

### Post by mazz0 on 2009-10-02
Seriously, me.isSooooooooStupid() == true!!!

---

### Post by Mighty_Joe on 2009-10-02
> **mazz0 said:**
> Seriously, me.isSooooooooStupid() == true!!!

Don't sweat it.  The reason I know the solution is because I've done the same thing a dozen times.

---

