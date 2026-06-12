---
title: "Shell command"
date: 2011-05-14
forum: General Help
---

### Post by layers on 2011-05-14
I am trying to instal something, according to the instructions, I am just supposed to say "sh setup.sh"
But when I do, I get ```
ibo@ibo-laptop:~/Desktop/h/HMM3-Linux$ sudo sh ./setup.sh
./setup.sh: 9: function: not found
x86
ibo@ibo-laptop:~/Desktop/h/HMM3-Linux$ 
```I think I have something that I have not yet installed on my system, because the same file had worked on my previous system build.

---

### Post by TeoBigusGeekus on 2011-05-14
The 9nth line of the script has a function that your system doesn't recognize.
If it's not very long, can you post us the contents of the script?

---

### Post by matt_symes on 2011-05-14
Hi

> **layers said:**
> I am trying to instal something, according to the instructions, I am just supposed to say "sh setup.sh"
But when I do, I get ```
ibo@ibo-laptop:~/Desktop/h/HMM3-Linux$ sudo sh ./setup.sh
./setup.sh: 9: function: not found
x86
ibo@ibo-laptop:~/Desktop/h/HMM3-Linux$ 
```I think I have something that I have not yet installed on my system, because the same file had worked on my previous system build.

What on earth are you trying to install ?

Can i suggest you read this ? It will help you to get answers quicker.

[https://help.ubuntu.com/community/GettingAnswers](https://help.ubuntu.com/community/GettingAnswers)

Kind regards

---

### Post by layers on 2011-05-14
```
#!/bin/sh
#
# Product setup script - Loki Entertainment Software

# Go to the proper setup directory (if not already there)
cd `dirname $0`

# Return the appropriate architecture string
function DetectARCH {
    status=1
    case `uname -m` in
        i?86)  echo "x86"
            status=0;;
        *)     echo "`uname -m`"
            status=0;;
    esac
    return $status
}

# Return the appropriate version string
function DetectLIBC {
      status=1
      if [ -f `echo /lib/libc.so.6* | tail -1` ]; then
          if fgrep GLIBC_2.1 /lib/libc.so.6* 2>&1 >/dev/null; then
                  echo "glibc-2.1"
                  status=0
          else    
                  echo "glibc-2.0"
                  status=0
          fi        
      elif [ -f /lib/libc.so.5 ]; then
          echo "libc5"
          status=0
      else
          echo "unknown"
      fi
      return $status
}

# Detect the Linux environment
arch=`DetectARCH`
libc=`DetectLIBC`

# Find the installation program
function try_run
{
    setup=$1
    shift
    fatal=$1
    if [ "$1" != "" ]; then
        shift
    fi

    # First find the binary we want to run
    failed=0
    setup_bin="setup.data/bin/$arch/$libc/$setup"
    if [ ! -f "$setup_bin" ]; then
        setup_bin="setup.data/bin/$arch/$setup"
        if [ ! -f "$setup_bin" ]; then
            failed=1
        fi
    fi
    if [ "$failed" -eq 1 ]; then
        if [ "$fatal" != "" ]; then
            cat <<__EOF__
This installation doesn't support $libc on $arch

Please contact Loki Technical Support at support@lokigames.com
__EOF__
            exit 1
        fi
        return $failed
    fi

    # Try to run the binary
    # The executable is here but we can't execute it from CD
    setup="$HOME/.setup$$"
    cp "$setup_bin" "$setup"
    chmod 700 "$setup"
    if [ "$fatal" != "" ]; then
        "$setup" $*
        failed=$?
    else
        "$setup" $* 2>/dev/null
        failed=$?
    fi
    rm -f "$setup"
    return $failed
}


# Try to run the setup program
status=0
rm -f "$setup"
if ! try_run setup.gtk && ! try_run setup -fatal; then
    echo "The setup program seems to have failed on $arch/$libc"
    echo
    echo "Please contact Loki Technical Support at support@lokigames.com"
    status=1
fi
exit $status

``` If I try commenting it out, the next function on line 21 gets flamed.

---

### Post by TeoBigusGeekus on 2011-05-14
Try
```
sudo bash ./setup.sh
```

---

### Post by layers on 2011-05-14
> **TeoBigusGeekus said:**
> Try
```
sudo bash ./setup.sh
```
thanks

---

### Post by TeoBigusGeekus on 2011-05-14
You're welcome mate.

---

### Post by layers on 2011-05-14
Is there a nicely general article about scripting and "bash" you might know? For a person who knows C, C++, assembly languages? I've never been properly introduced to them.

---

### Post by TeoBigusGeekus on 2011-05-14
[There]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") you go.

---

### Post by 5149.5 on 2011-05-14
You could start[ here]("http://goo.gl/Z1oTf").

---

