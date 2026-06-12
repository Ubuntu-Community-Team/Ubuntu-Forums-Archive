---
title: "java class not found - joda time"
date: 2011-06-06
forum: General Help
---

### Post by mistertransistor on 2011-06-06
I'm using Ubuntu 11.04 and NetBeans 7.0. I'm completely puzzled by this. I've created a test application to reproduce it ...

package test;
import  TimeUtils.*;
public class Test {
    public static void main(String[] args) {
        System.out.println(TimeUtils.MillisToUTCDateTimeString(0));
    }
}

TimeUtils is a static class of mine in a separate NetBeans project ...

package TimeUtils;
import  org.joda.time.DateTimeZone;
import  org.joda.time.DateTime;
import  org.joda.time.format.*;

public abstract class TimeUtils {

    public static String MillisToUTCDateTimeString(long millis) {
        DateTimeFormatter fmt = DateTimeFormat.forPattern("yyyy-MM-dd-HH-mm-ss.SSS");
        DateTimeZone zoneUTC = DateTimeZone.UTC;
        DateTime dtUTC = new DateTime(millis, zoneUTC);
        return fmt.print(dtUTC);
    }
  ... a few other static methods

When I use this under NetBeans it's fine and prints
1970-01-01-00-00-00.000
The joda time jar is in both jre/lib and jdk/lib/ext, and TimeUtils is specified as a library in the test project so that the import works.

When I run it under terminal with java -jar test.jar I get an error

Exception in thread "main" java.lang.NoClassDefFoundError: org/joda/time/ReadableInstant
    at test.Test.main(Test.java:20)
Caused by: java.lang.ClassNotFoundException: org.joda.time.ReadableInstant
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
   etc etc

I have tried everything I can think of but cannot fix this. I have even specified the joda time jar explicitly using java -cp <joda.jar>  without any effect.

I do not have a CLASSPATH environment variable. But I've tried it without success.

Please help! It's probably a silly newbie error ...

---

### Post by mistertransistor on 2011-06-09
Well, that's a disappointing response.

After a bit of digging around I found:  

1. when you specify 'java -jar' it completely ignores your classpath. This is specified in the java documentation [http://java.sun.com/j2se/1.4.2/docs/tooldocs/linux/java.html](http://java.sun.com/j2se/1.4.2/docs/tooldocs/linux/java.html) but is NOT clear from the 'help' you get by typing just 'java'. 

2. that means that the jar must contain all classes it requires. To get  netBeans to include the joda jar, select the project and add the joda  jar using properties / categories - libraries / compile tab - add JAR /  folder.  

Thanks again.

---

