---
title: "Ubuntu Live cd - edit firefox settings (mimetypes)"
date: 2011-09-14
forum: General Help
---

### Post by mike28486 on 2011-09-14
I honestly could not think of a proper title to this topic.  Here is what I am trying to do,

I am creating an Ubuntu Live disc (10.10) for my customers for when their system has been corrupted and they need me to remote connect to it.  The web based app I use is screenconnect and it uses Java (Sun) to make a connection to a linux machine.  I have all of this setup correctly and am now fine tuning and making it more efficient, which lads to my problem.

When firefox downloads an application and asks to run/open or save I want it to open the file automatically with Java.  I know this is done and edited in the Mimetypes.rdf file but what I need to do is have that file with the correct parameters to already be wrapped into the disc.  As far as I can tell the location of the file goes to /home/ubuntu/.mozilla/firefox and then to a profile.default folder.  I am sure I can inject the new mimetypes.rdf file to the default profile but it seems firefox creates a random string of characters before the .default that changes everytime the cd is launched.

What I am looking for is being able to take a pre-done mimetypes.rdf and inject it into the firefox default profile and then I can wrap it into an ISO (which I already know how to do) so that when a user boots up and runs firefox to start my remote connection it automatically opens the file rather than needing the customer to choose to run the file.

I hope what I have said makes some sense.

-Mike

---

