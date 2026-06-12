---
title: "access ubuntu without gui"
date: 2010-07-03
forum: General Help
---

### Post by ororo on 2010-07-03
I have the following need.
I would like to have 3 distinct entries for Ubuntu in the GRUB menu. The first two entries are the usual ones: multi-user with GUI and single-user without GUI. The third one should be a multi-user *without* GUI: for example, accessing directly to tty 2. I don't know how to obtain this.

Is there any kernel option telling the kernel which tty use default ? 

If not, is there any kernel option telling the kernel which runlevel to use default ? for example, I could remove the gdm init script in level 5, so that runlevel 2 and 5 lead to distinct results.

Or also, within a init script, is there any way to see which kernel options were used?


thank you!

---

### Post by sisco311 on 2010-07-03
> **ororo said:**
> 

If not, is there any kernel option telling the kernel which runlevel to use default ? for example, I could remove the gdm init script in level 5, so that runlevel 2 and 5 lead to distinct results.



Yes, simply append the linux line (GRUB2) or kernel line (GRUB legacy) with the number of the runlevel.  But since 9.10 GDM is started by an Upstart job, not by a System-V style init script. Upstart still emulates the runlevels but there is an easier way to disable GDM, you have to append **text** the linux (or kernel) line. If you are using GRUB2, then edit the /etc/grub.d/10_linux file to look like this:
```
...
  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
        "single ${GRUB_CMDLINE_LINUX}"
  fi

[B]#TEXT MODE
  linux_entry "${OS}" "${version} (text mode)" false \
       "text ${GRUB_CMDLINE_LINUX}"
#EDN TEXT MODE[/B]

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done
```

Then run:
```
sudo update-grub
```

---

### Post by ororo on 2010-07-03
Great!
It works, thank you.

---

