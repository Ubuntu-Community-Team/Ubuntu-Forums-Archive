---
title: "update-apt-xapi?"
date: 2010-11-09
forum: General Help
---

### Post by armageddon08 on 2010-11-09
Hi all. I'm using Ubuntu 10.10. Is there any way to stop this process update-apt-xapi from starting up at random moments and using 95-100% of my CPU. Although it does not last long, still at those times the fan starts blowing like anything; so it's kinda annoying.

---

### Post by ajgreeny on 2010-11-15
You can re-nice the application to make it more "nice", ie have a lower priority in the system's scheme of things, or if you are prepared to run update manager manually you can even remove the application **apt-xapian-index**

---

