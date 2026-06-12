---
title: "Standby and cpu scaling issues on GA-965P-DS4"
date: 2010-07-25
forum: General Help
---

### Post by P4man on 2010-07-25
Hi,

I recently changed my motherboard to a gigabyte GA-965P-DS4; and ever since I can not go in to standby anymore. it worked fine with my old motherboard.

I had similar issues with windows; but a bios upgrade fixed it for windows. any clues what I can do to fix it in ubuntu (10.04)?

Possibly related; when i overclock my cpu; I lose cpu scaling in ubuntu. It always runs at full speed. The cpu scaling applet  says "CPU frequency scaling unsupported". When I disable manual FSB control in the bios it works fine (and it works fine in windows even when overclocked).

Any pointers would be much appreciated.

update:
sudo s2ram -f  
works! After installing uswsusp. I guess that will do for standby, remains the cpu scaling question.

---

