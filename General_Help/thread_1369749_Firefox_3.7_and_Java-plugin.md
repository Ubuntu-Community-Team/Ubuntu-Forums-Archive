---
title: "Firefox 3.7 and Java-plugin"
date: 2010-01-01
forum: General Help
---

### Post by Krause on 2010-01-01
Anyone know how to get the sun java plugin to work with firefox 3.7? Any files I need to copy over to a different folder or anything?

I just installed Firefox 3.7 from the Mozilla Daily PPA and thats the only thing currently not showing up.

Thank you

---

### Post by Krause on 2010-01-01
After some searching I found an answer that works.

make a symbolic link in your mozilla plugins directory (~/.mozilla/plugins) like this:
ln -s /usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64/libnpjp2.so libnpjp2.so

and ten in the new firefox/minefield in the url bar type about:config
it will give you a warning that modifying these settings can be dangerour, hit the button that says you will be carfull.

Then in the filter type java

go to the value called "java.java_plugin_library_name" and right click it and select modify.

Change the name to "libnpjp2" without the quotes.

restart firefox and your done, java will now be working.

---

