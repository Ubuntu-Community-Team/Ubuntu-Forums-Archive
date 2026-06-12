---
title: "How do I get the Java applet installed and working?"
date: 2011-01-13
forum: General Help
---

### Post by 1chess2u Christian on 2011-01-13
Please tell me if there is someone who asked the same question, but I have the Ubuntu 10.10 net-book remix version, and every time that I go to try to download and install the Java applet, it will download Ok (I think), but when I try to open the file, there are no errors, but it won't open. When I try to re-download, it does nothing again. Please help me!

---

### Post by mikewhatever on 2011-01-13
1. Add the partner repository.
```
sudo apt-add-repository 'deb http://archive.canonical.com/ubuntu maverick partner'
```

2. Install Sun Java.
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

3. Verify that java is installed.
[http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

I seem to have misunderstood the question slightly. What applet were you trying to install? Did you install java?

---

### Post by 1chess2u Christian on 2011-01-14
I thank you, but when I typed in the first line of code into the terminal, it said, "Error: need a repository as argument." I was just trying to download the Java applet from the internet, as I did not find it in the software center (without it I cannot run Java applications on the Internet, and this is a big problem for me, because I need to use some of these applications for school.)

---

### Post by mikewhatever on 2011-01-14
The question is whether you have java installed or not. You need it installed to run java applets.
I've edited the command above, so that it should work now.

---

