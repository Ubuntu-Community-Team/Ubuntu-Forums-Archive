---
title: "dev/null permission problems"
date: 2012-09-29
forum: General Help
---

### Post by addisonElliott on 2012-09-29
Hello, I am having a issue with my ubuntu server. I have noticed errors about permission denied for dev/null and dev/random in some of the processes running. The issue is that when the server is first started it sets the permissions on dev/null to 600. 

The permissions need to be 660 at least and 666 preferably. I have checked the permissions for udev, and it does have the correct permission for it(660). Whenever I call "udevadm trigger", it sets the permissions on everything correctly.

Does anyone have any insight on what could be the issue? I'm not sure if something is overwriting udev or if udev isn't running correctly in the first place.

---

