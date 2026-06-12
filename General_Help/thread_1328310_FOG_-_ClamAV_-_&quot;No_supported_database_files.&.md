---
title: "FOG - ClamAV - &quot;No supported database files.&quot;"
date: 2009-11-16
forum: General Help
---

### Post by Roasted on 2009-11-16
Long story short... got a FOG server running here (Ubuntu 9.04 64 bit + FOG 0.28) which FOG has built in PXE boot support to scan computers with ClamAV.

When I network boot the computers via PXE that I want to scan, I get an error about ClamAV, no database files found in /usr/local/share/clamav.

I keep googling and people are saying "just update ClamAV with sudo freshclam" and I did, but the error persists. How do I fix this?

---

### Post by phillw on 2009-11-16
> **Roasted said:**
> Long story short... got a FOG server running here (Ubuntu 9.04 64 bit + FOG 0.28) which FOG has built in PXE boot support to scan computers with ClamAV.

When I network boot the computers via PXE that I want to scan, I get an error about ClamAV, no database files found in /usr/local/share/clamav.

I keep googling and people are saying "just update ClamAV with sudo freshclam" and I did, but the error persists. How do I fix this?

Try re-installing it via synaptics. It may have gotten 'confused'

Regards,

Phill.

---

