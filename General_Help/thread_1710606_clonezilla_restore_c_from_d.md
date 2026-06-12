---
title: "clonezilla restore c: from d:"
date: 2011-03-20
forum: General Help
---

### Post by gus2986 on 2011-03-20
Hello,
The idea is to restore C:/ windows xp from D: ubuntu clonezilla 10-10 GRUB 2 Automatic restore by booting menu but after a week I get working clonezilla with some problems:
EOF
echo "RESTORE PC2" >&2
cat << EOF
menuentry "RESTORE PC2" {
insmod part_msdos
insmod fat
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 140c-3521
loopback loop /ubuntu/iso/clonezilla-live-20110113-maverick.iso
set root=(loop)
linux (loop)/live/vmlinuz boot=live live-config union=aufs nolocales noprompt gfxpayload=800x600x16 
ip=frommedia nosplash toram=filesystem.squashfa 
ocs_live_run="ocs-live-restore"
ocs_live_extra_param="-g en_US.UFT-8 -t -k NONE -g auto -e1 auto -e2 -b -c restoreparts serge-image sda1" 
initrd (loop)/live/initrd.img
}
EOF 

Problem1: Runs manual, clonezilla is not taking the parameters to run automatic. 
Problem2: Clonezilla runs ONLY with a USB clonezilla boot format, connected to a usb port.
Thanks for help.

---

### Post by gus2986 on 2011-03-20
Correction: parameters with /"/" BUT CLONEZILLA STILL WITHOUT take parameters.
echo "RESTORE PC2" >&2
cat << EOF
menuentry "RESTORE PC2" {
    insmod part_msdos
    insmod fat
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 140c-3521
    loopback loop /ubuntu/iso/clonezilla-live-20110113-maverick.iso
    set root=(loop)
    linux (loop)/live/vmlinuz boot=live live-config union=aufs nolocales noprompt gfxpayload=800x600x16
    ip=frommedia nosplash toram=filesystem.squashfa    
    osc_live_run=\"osc-live-general\"
    osc_live_extra_param=\"\" 
    osc_live_keymap=\"\"
    osc_prerun=\"\" 
    osc_lang=\"en_US.UFT-8\"
    initrd (loop)/live/initrd.img
}
EOF

osc_lang=\"en_US.UFT-8\" not received   (!^%$&*^(*$$$!!](*,))

---

### Post by gus2986 on 2011-03-20
Correction: parameters with /"/" BUT CLONEZILLA STILL WITHOUT take parameters.
echo "RESTORE PC2" >&2
cat << EOF
menuentry "RESTORE PC2" {
insmod part_msdos
insmod fat
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 140c-3521
loopback loop /ubuntu/iso/clonezilla-live-20110113-maverick.iso
set root=(loop)
linux (loop)/live/vmlinuz boot=live live-config union=aufs nolocales noprompt gfxpayload=800x600x16
ip=frommedia nosplash toram=filesystem.squashfa 
ocs_live_run=\"osc-live-general\"
ocs_live_extra_param=\"\" 
ocs_live_keymap=\"\"
ocs_prerun=\"\" 
ocs_lang=\"en_US.UFT-8\"
initrd (loop)/live/initrd.img
}
EOF

still not receiving parameters...

---

