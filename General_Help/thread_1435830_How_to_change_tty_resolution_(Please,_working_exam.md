---
title: "How to change tty resolution? (Please, working examples only!)"
date: 2010-03-21
forum: General Help
---

### Post by prodigy_ on 2010-03-21
Ok, I'm sick of Grub2. It's a total mess that is needlessly complicated in the worst fashion imaginable. (Yes, I've read [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2), it doesn't help.) I can't understand Grub2 developers thinking (maybe they're aliens?) and, quite frankly, I just don't care anymore.

A simple question: how to change resolution for textmode terminals (tty1, tty2, ...)? I don't want to read any more [censored] about gfxpayload and how it's supposed to work. Please don't respond if you can't provide an **example** config that **simply just works**.

---

[Edit/SOLVED]: No longer an issue in Lucid Lynx for me. See [this HOWTO](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml). Note that 1280x1024 isn't the only option. You can use any resolution supported by VBE of your video card. Use **vbeinfo** command in Grub shell to see the list of available display modes.

---

### Post by Brandon Williams on 2010-03-23
When you say that you want to change the console resolution, do you really mean that you want to change the font size? If so, then run 'sudo dpkg-reconfigure console-setup'. Keep pressing enter until you get to the dialog that lets you configure the font for the console. If you are using a framebuffer for the console (run 'lsmod | grep fbcon' if you're not sure), then you will want to select either Terminus or TerminusBold. In the next screen, select the desired font size. Then press enter until you get to the end and it generates the new initramfs. After it's done, switch to a console and run setupcon on the command line to see if you like the setting you selected.

As you note, there is various documentation that indicates that it should be possible to do this all with the grub config. I haven't tried that, though, since the above method works to change the font size.

---

### Post by Brandon Williams on 2010-03-24
After looking at this post, I went back and looked at this again to try to get a different resolution without reconfiguring console-setup (I don't really like the Terminus font). [Here is my post](http://ubuntuforums.org/showpost.php?p=9020830&postcount=10) that details the changes I made.

The method works for Lucid. If you are using Karmic, it might not, since KMS is not enabled by default in Karmic and the GRUB_GFXPAYLOAD_LINUX variables in /etc/default/grub is not supported there either. My solution for Lucid has all the right elements, though: 1. make sure KMS is not enabled; 2. set GRUB_GFXMODE to the resolution you want; 3. set gfxpayload=keep. In Karmic, you probably don't need to do anything for #1 unless you previously turned on KMS. For #3, add the GRUB_GFXPAYLOAD_LINUX setting to your /etc/default/grub file and then modify /etc/grub.d/10_linux to add support for the variable. Here is a snippet from my 10_linux file with the relevant code:
```
    title="$(gettext "%s, with Linux %s (recovery mode)")"
  else
    title="$(gettext "%s, with Linux %s")"
  fi
  printf "menuentry \"${title}\" ${CLASS} {\n" "${os}" "${version}"
  cat << EOF
	recordfail
EOF
  save_default_entry | sed -e "s/^/\t/"

[B]  if [ "x$GRUB_GFXPAYLOAD_LINUX" != x ]; then
	  cat << EOF
	set gfxpayload=$GRUB_GFXPAYLOAD_LINUX
EOF
  fi[/B]

  if [ -z "${prepare_boot_cache}" ]; then
    prepare_boot_cache="$(prepare_grub_to_access_device ${GRUB_DEVICE_BOOT} | sed -e "s/^/\t/")"
  fi
  printf '%s\n' "${prepare_boot_cache}"
  if [ "x$5" != "xquiet" ]; then
    cat << EOF
	echo	$(printf "$(gettext "Loading Linux %s ...")" ${version})
```

I don't have a Karmic box to test this on any more, but it produces a working config on Lucid and will most likely function on Karmic, too.

---

### Post by prodigy_ on 2010-04-07
Thanks! I'll test your script today.

> GRUB_GFXPAYLOAD_LINUX variables in /etc/default/grub is not supported there either.
So that's why "vga=xxx" works (even though you get a message about it being deprecated) while "set gfxpayload" doesn't?

---

