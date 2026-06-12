---
title: "home partition wont mount 'exec'"
date: 2010-01-31
forum: General Help
---

### Post by cmoloney on 2010-01-31
Hi, I'm new here so I'm not sure which category this should be posted in.

  I'm having trouble getting the home partition to mount 'exec'.  I have a few odd tools I keep in ~/bin (mostly little bash scripts).  Since I don't use them that often I'm not sure when the problem first arose. It's definitely present now that I've up graded to 9.10 but it may have been present in 9.04 and I didn't notice.
  My fstab has the line:
/dev/sda3  /home   ext3  rw,nosuid,nodev,exec,auto,user,async,users,relatime 0  2
and I've also tried variations with 'defaults',exec   etc.  It is easily fixed after I log in via
  sudo mount -o remount,exec /home
but the initial mount during boot always leaves /home as 'noexec'.

 Any ideas where to look next? Anything else I should supply to help track it down?

(There's nothing obvious in dmesg or /var/log/messages, except lots of "Jan 31 15:38:02 erin pulseaudio[2722]: ratelimit.c: 697 events suppressed")

Output from mount shows:
  /dev/sda3 on /home type ext3 (rw,noexec,nosuid,nodev,relatime)
and /proc/self/mounts has
 /dev/sda3 /home ext3 rw,noexec,nosuid,nodev,relatime,errors=continue,data=writeback 0 0


Colin.

---

