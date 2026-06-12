---
title: "Choosing to start X during bootup"
date: 2010-07-13
forum: General Help
---

### Post by cci[RR]us on 2010-07-13
Hi,

In the past (before UpStart was used in Ubuntu) I was able to configure multiple boot items in Grub menu to load the same kernel but into different runlevels. I had configured runlevel 3 (I went into /etc/rc3.d/ and removed the symlink to /etc/init.d/gdm) to be w/o GDM, so that if I had chosen it, my box would not boot into X.

How can I achieve the same effect in Lucid?

---

### Post by sisco311 on 2010-07-13
In order to boot without starting the display manager use the **text** kernel parameter.


To create a *text mode* Grub2 menu entry:

[list=i]
[*]backup the /etc/grub.d/10_linux file:
```
sudo cp /etc/grub.d/10_linux{,-backup}
sudo chmod -x /etc/grub.d/10_linux-backup
```

[*]open it for editing:
```
gksu gedit /etc/grub.d/10_linux
```

[*]scroll down to the **linux_entry** function (line ~64), and edit it to look like this:
```

...
linux_entry ()
{
  os="$1"
  version="$2"
  recovery="$3"
  args="$4"

[B]  if [ "${recovery}" = "text" ]; then
    title="$(gettext_quoted "%s, with Linux %s (text mode)")"
  elif ${recovery} ; then
    title="$(gettext_quoted "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext_quoted "%s, with Linux %s")"
  fi[/B]
  printf "menuentry '${title}' ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
...
```

[*]scroll down to the end of file and call the function:
```

...
  linux_entry "${OS}" "${version}" false \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}" \
      quiet

[B]  linux_entry "${OS}" "${version}" "text" \
      "text ${GRUB_CMDLINE_LINUX}"
[/B]
  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}" "${version}" true \
        "single ${GRUB_CMDLINE_LINUX}"
  fi

  list=`echo $list | tr ' ' '\n' | grep -vx $linux | tr '\n' ' '`
done


```

[*]generate a new grub.cfg file:
```
sudo update-grub
```

[*]check out the /boot/grub/grub.cfg file and see if the new menu entry is generated.
[/list]

If something went wrong, restore the original settings:
```
sudo cp /etc/grub.d/10_linux{-backup,}
sudo chmod +x /etc/grub.d/10_linux
```
```
sudo update-grub
```

---

### Post by cci[RR]us on 2010-07-20
> **sisco311 said:**
> In order to boot without starting the display manager use the **text** kernel parameter.
Thanks!!! You have been of great help! :)

---

