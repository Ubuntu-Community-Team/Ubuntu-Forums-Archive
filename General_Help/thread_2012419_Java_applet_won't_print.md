---
title: "Java applet won't print"
date: 2012-06-29
forum: General Help
---

### Post by AlmaTlust on 2012-06-29
Hi,
I have created a nice graphical wordlist under [http://www.wordle.net/create](http://www.wordle.net/create)
and would like to print it. However, I can't. The print dialogue won't even show up. I tried different browsers, but to no avail. I heard that on a Mac the same problem can happen because of policy reasons. Would this be the problem, and if yes, how do I solve it?
Thanks in advance for any help

---

### Post by greazeball on 2013-05-06
I am having the same problem.  I'd like to print to a pdf so I can get a vector version of my wordle, but the "print" button does nothing.  Like AlmaTrust, the only information I can find about this problem is a fix for Mac users on this page: [http://www.wordle.net/macprint](http://www.wordle.net/macprint)  They suggest the following:

> The application will ask you for permission to create the file .java.policy in your "home" directory, or modify the file if it already exists. It will add the following text to that file:


grant codeBase "http://wordle.appspot.com/-" {
	permission java.net.SocketPermission "localhost:631", "connect,resolve";
	permission java.lang.RuntimePermission "queuePrintJob";
};
Once it has run, you'll have to quit any currently running browsers, and start them up again. Printing should work for you from that point on.


Will this work in Ubuntu 12.04?  Where can I make this .java.policy or equivalent file?

---

### Post by greazeball on 2013-05-07
I can confirm that the above method does not work, has anyone had to print through a java applet before?

---

