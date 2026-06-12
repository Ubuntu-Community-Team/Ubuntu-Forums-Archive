---
title: "Thunderbird doesn't open unless &quot;gksudo thunderbird&quot;"
date: 2010-10-12
forum: General Help
---

### Post by lethalfang on 2010-10-12
Ok, this is odd. I've upgraded to 3.14 via ubuntuzilla a few days ago, and now I can't open thunderbird as a regular user, only as root when I type in "gksudo thunderbird" in the terminal. 
Does anyone else have that issue, or is it just me?

---

### Post by lethalfang on 2010-10-16
Bump.
Anyone has any idea?
I type "thunderbird" in the terminal, and nothing happens. Thunderbird only opens when I type "gksudo thunderbird."

I went to the script file /opt/thunderbird/thunderbird, commented the set -x for debugging, and the only difference in output between "gksudo thunderbird" and "thunderbird" is the exit code.

---

