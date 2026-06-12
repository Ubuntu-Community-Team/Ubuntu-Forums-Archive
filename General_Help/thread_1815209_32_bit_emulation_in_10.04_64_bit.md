---
title: "32 bit emulation in 10.04 64 bit"
date: 2011-07-30
forum: General Help
---

### Post by aznranndydraman on 2011-07-30
Hi, sorry if this question has been asked, but I didn't have the luck of finding relevant posts easily through search.

I'm trying to install smlnj 110.73 on a 64 bit lucid, and during installation, it complains of no 32-bit support.

Having zero knowledge of how 32-bit emulation is triggered in Ubuntu, all the leads I have to go on is this piece of shell script used by the installer to determine the architecture and emulation:

```

#
# on 64-bit linux systems, we need to check to see if the 32-bit emulation
# support is installed
#
if [ x"$ARCH" = "xx86" -a x"$OPSYS" = "xlinux" ] ; then
  case `uname -m` in
    x86_64)
      tmpFile=smlnj-test$$
      echo "int main () { return 0; }" >> /tmp/$tmpFile.c
      gcc -m32 -o /tmp/$tmpFile /tmp/$tmpFile.c 2> /dev/null 1>> /dev/null
      if [ "$?" != "0" ] ; then
	rm -f /tmp/$tmpFile /tmp/$tmpFile.c
	complain "$this: !!! SML/NJ requires support for 32-bit executables"
      else
	rm -f /tmp/$tmpFile /tmp/$tmpFile.c
      fi
    ;;
    *) ;;
  esac
fi

```

I'm going to work away on this piece (not a sh script guru either), but in the mean time if a kind expert can offer some help it would be appreciated...a lot. :)

Thanks.

---

### Post by IWantFroyo on 2011-07-30
I don't know about the program you mentioned, but the ia32 package lets 32 bit apps run fine under Ubuntu.

---

### Post by aznranndydraman on 2011-07-30
Thanks for the quick reply! Will try and let you know.

---

### Post by aznranndydraman on 2011-07-31
Thanks IWantFroyo! ia32 helped.

To elaborate, the problem is with the -m32 option for gcc on 64 bit Ubuntu. The complete set of packages installed to unblock installation was:
```
gcc-multilib g++-multilib ia32-libs
```

---

