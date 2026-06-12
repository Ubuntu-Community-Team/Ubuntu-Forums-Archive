---
title: "Java keyboard shortcuts focus"
date: 2010-11-19
forum: General Help
---

### Post by MrNatewood on 2010-11-19
Using firefox,chromnium and opera to do homework in a java applet the "Tab" keyboard button does not function as expected.

It seems as though it does not focus on the applet, ever.

Instead of having the expected behavior of tabbing between the homework boxes it is used to change selection focus on the browser(from the address bar to other 2 things I can't recognize).

Anyone knows a workaround for this?

Using sun-java 64-bit. doesn't work with openJDK also.
On the windows version of firefox+java32&explorer+java64 this works fine.

---

### Post by forestG on 2010-12-02
try this in your .bashrc file in your home folder or in /etc/profile

add this line at the end

export GDK_NATIVE_WINDOWS=1

---

### Post by MrNatewood on 2010-12-03
Added to both .bashrc and /etc/profile without any change.

---

