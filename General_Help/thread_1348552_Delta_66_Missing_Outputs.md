---
title: "Delta 66 Missing Outputs"
date: 2009-12-07
forum: General Help
---

### Post by eyeprotocol on 2009-12-07
Hello

In order to get my M-Audio Delta 66 working on Ubuntu 9.10, i had to type this line in /etc/modprobe.d/alsa-base.conf:

options snd-ice1712 model=delta66

Now, the card appears under Preferences -> Sound -> Hardware, and actually produces sound, coming out of the SPDIF coaxial output.

Unfortunately, all the possible inputs or outputs that appear under Preferences -> Sound -> Input or Preferences -> Sound -> Output are the digital ones. The analog ones are missing (the card has 4 + 4 of them).

I am not an expert, but i understand that alsa is not aware of the extra inputs / outputs. How can i resolve this issue?

Kind Regards

---

