---
title: "grub2 - can't get rid of recovery mode menuentries for other os automatically"
date: 2009-11-06
forum: General Help
---

### Post by bluesscream on 2009-11-06
How can we prohibit update-grub from drawing up additional recovery mode menuentries  for all kernels of os' on second(third...) partitions and drives by default? Editing /etc/default/grub does this by uncommenting line 'GRUB_DISABLE_LINUX_RECOVERY="true"' for grub2's system partition, but this does not affect the other os' on my multiboot/multipartition machine.

Editing 30_os-prober following  this tutorial (- tx drs305, ranch hand and the others) :
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)


```
        LINITRD="`echo ${LINUX} | cut -d ':' -f 5`"
        LPARAMS="`echo ${LINUX} | cut -d ':' -f 6- | tr '^' ' '`"
# User-added variables
        nosingle="`echo ${LPARAMS} | sed 's/^.* //'`"
        


        if [ -z "${LLABEL}" ] ; then
          LLABEL="${LONGNAME}"
        fi

        
        if  [ ${nosingle} = "single" ]; then
       break 
    fi

        cat << EOF
menuentry "${LLABEL} (on ${DEVICE}" \
EOF
```



removes menuentry recovery mode but gives only one menuentry for just one kernel for each probed os. 
Did I overlook something?

---

