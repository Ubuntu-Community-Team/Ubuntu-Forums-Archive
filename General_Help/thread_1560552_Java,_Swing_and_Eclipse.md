---
title: "Java, Swing and Eclipse"
date: 2010-08-25
forum: General Help
---

### Post by Adrienk on 2010-08-25
I recently installed the JDK 6 and Eclipse both via the terminal but there doesnt seem to be any java swing.....

Any tips on installing it?

Should it not already come with Eclipse/JDK 6?

This is for Ubuntu 10.4

---

### Post by Adrienk on 2010-08-25
Bump

---

### Post by akoskm on 2010-08-25
> **Adrienk said:**
> I recently installed the JDK 6 and Eclipse both via the terminal but there doesnt seem to be any java swing.....

Any tips on installing it?

Should it not already come with Eclipse/JDK 6?

This is for Ubuntu 10.4

Yes, it comes together with the JDK. Why do you think that there is no Swing?
Have you tried to import the swing package?
```

import javax.swing.*;

```.

---

### Post by Adrienk on 2010-08-25
Yes, I would not have posted this question if I did not try that. its the only thing I use to build GUIS, I think awt is a joke.

any ways.

There is java security and sql and thats it for my JDK6 install.

---

### Post by Adrienk on 2010-08-25
And the only Jar files in the library build path are JDK6, I have both the JRE and JDK 6 installed and I only get Java.security and Java.SQL

---

### Post by Adrienk on 2010-08-25
bump

---

### Post by Nytram on 2010-08-25
Do you mean there's no way to design a Swing GUI using Eclipse?

I've never used Eclipse before but I believe it's not possible, there's an IDE called Netbeans which allows GUI building (in the same way as Visual Studio.)

(If I understand your problem correctly.)

---

### Post by Adrienk on 2010-08-25
Nope:

I installed Open JDK 6
I installed the  JRE 6
I installed Eclipse

I went:

java.s -> this brought a drop down list of security and SQL but no swing.

If i install eclipse in windows and JDK 6 I get java security, sql and swing.

I refuze to use netbeans to design something, its code is far far to bloated.

I just want swing to be in the drop down list for imports

---

### Post by Adrienk on 2010-08-26
bump

---

### Post by akoskm on 2010-08-26
> **Adrienk said:**
> Nope:

I installed Open JDK 6
I installed the  JRE 6
I installed Eclipse

I went:

java.s -> this brought a drop down list of security and SQL but no swing.

If i install eclipse in windows and JDK 6 I get java security, sql and swing.

I refuze to use netbeans to design something, its code is far far to bloated.

I just want swing to be in the drop down list for imports

This is beacuse Swing is imported from java**x**```
import javax.swing.*;
``` and not from ```
java.s
```.

---

