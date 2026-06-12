---
title: "Problem Installing Axigen on 10.04 LTS"
date: 2012-01-11
forum: General Help
---

### Post by n00blawl on 2012-01-11
When I try to install Axigen on my VPS with 10.04 I get the following error:

[B]dpkg: regarding .../axigen_8.0.1-1_i386.deb containing axigen:
 sendmail-bin conflicts with mail-transport-agent
  axigen provides mail-transport-agent and is to be installed.
dpkg: error processing /tmp/axigen-8.0.1.i386.deb.run.a6bFW1/axigen-8.0.1/axigen_8.0.1-1_i386.deb (--install):
 conflicting packages - not installing axigen
Errors were encountered while processing:
 /tmp/axigen-8.0.1.i386.deb.run.a6bFW1/axigen-8.0.1/axigen_8.0.1-1_i386.deb[/B]

I'm not sure how to resolve this, I've tried removing sendmail by using the commant apt-get remove sendmail. Any ideas? Thanks in advance!

I've also combed the Axigen forums but can't find anything on this error.

---

