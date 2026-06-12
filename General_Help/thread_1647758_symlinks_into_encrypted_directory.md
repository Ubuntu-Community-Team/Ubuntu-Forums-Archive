---
title: "symlinks into encrypted directory"
date: 2010-12-17
forum: General Help
---

### Post by enneract on 2010-12-17
Can anyone shed some light on what the behavior would be if I symlinked a non-encrypted directory (lets call it /media/sdcard/foo) into an encrypted home directory (lets say /home/documents/sdcard-docs)

Would files written to that symlinked directory be encrypted\garbled, or would they be normal? would files that were attempted to be read be interpreted as encrypted, or would they be read properly?

---

### Post by Dave_L on 2010-12-17
I just tested this, and the file was not encrypted.

---

