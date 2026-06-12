---
title: "Set default mime type associations for Firefox for all users"
date: 2012-08-19
forum: General Help
---

### Post by 7@m3 G33k on 2012-08-19
I am setting up Ubuntu PCs in a university environment for student use and I would like to configure mime type application associations for all users, one example being if a user clicks on a link in Firefox to a jnlp applet (e.g. [http://docs.oracle.com/javase/tutorialJWS/uiswing/components/ex6/RadioButtonDemo.jnlp](http://docs.oracle.com/javase/tutorialJWS/uiswing/components/ex6/RadioButtonDemo.jnlp)) I would like that to be launched with javaws.

So far the only solutions that I've found involve a login scrip that copies a custom mimeTypes.rdf file to the user's Firefox profile (~/.mozilla/firefox/xxxxxxxx.default/) but this is a bit clunky and means that users cannot make persistent modifications to preferences set in this way.

I have tried placing the mimeTypes.rdf file in various promising locations like /etc/firefox, /etc/firefox/prefs, /usr/lib/firefox, /usr/lib/mozilla & /usr/lib/mozilla-firefox but none of these work. Is this not possible or have I not found the right directory?

So far I've tried this on Ubuntu 10.04 x64 and for comparison Kubuntu 12.04 x64 - both seem to have the same directory structure for Firefox and I've failed to make either work as I want.

---

