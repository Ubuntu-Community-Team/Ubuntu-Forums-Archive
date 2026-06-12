---
title: "Waiting indefinitely at GRUB screen"
date: 2011-07-19
forum: General Help
---

### Post by gnaget on 2011-07-19
I have several servers running Ubuntu Desktop.  These servers are remote access only, and do not have a monitor or keyboard attached normally.  I'm running into problems with them occasionally getting hung up, after crashing, on the grub recovery mode screen.  The only way for me to make them boot up is to hook up a keyboard and hit enter.

My /etc/default/grub file is default:
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

What do I need to change to disable the grub loader screen from coming up automatically ever, or at least to make the timeout work when it does happen?

---

### Post by Alan F on 2011-07-19
"Recordfail timeout" is waiting for input from you. You can over-ride this by modifying as follows

In     etc//grub.d/00_header

make_timeout () 
{ 
    cat << EOF 
if [ "\${recordfail}" = 1 ]; then 
  set timeout=1 #was-1 
else 
  set timeout=${2} 
fi 
EOF 

With the "set timeout" at -1 it will wait indefinitely for your input. With it set at 1 it will continue automatically after 1 sec.

---

### Post by gnaget on 2011-07-28
> **Alan F said:**
> "Recordfail timeout" is waiting for input from you. You can over-ride this by modifying as follows

In     etc//grub.d/00_header

make_timeout () 
{ 
    cat << EOF 
if [ "\${recordfail}" = 1 ]; then 
  set timeout=1 #was-1 
else 
  set timeout=${2} 
fi 
EOF 

With the "set timeout" at -1 it will wait indefinitely for your input. With it set at 1 it will continue automatically after 1 sec.


I tried a variant of that, and it doesn't work.  They still hang indefinitely at the grub screen:

```

make_timeout ()
{
    cat << EOF
  set timeout=${2}
EOF
}

```

---

### Post by gnaget on 2011-07-31
can I get a bump please?

---

