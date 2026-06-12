---
title: "libXm.so.4 not found - tried all online guides"
date: 2011-11-30
forum: General Help
---

### Post by christia on 2011-11-30
Hi, i am trying to get my citrix client to work, i keep getting this error: "libXm.so.4 not found"

i followed this guide, but it still seems i can't get that library to be found... any ideas? using ubuntu 11.10

[https://help.ubuntu.com/community/CitrixICAClientHowTo](https://help.ubuntu.com/community/CitrixICAClientHowTo)

---

### Post by gordintoronto on 2011-11-30
The guide contains many parts. What steps did you follow? Is your 11.10 64-bit or 32-bit? From browsing posts on the Citrix forums, it appears that getting it working on a 64-bit install is an overwhelming challenge.

---

### Post by KaiO on 2011-12-09
Yeah. That one's a real pain.
I am running Kubuntu 11.10 64-bit.

These are the steps I had to do in order to get my client to work:
(Everything is done in the terminal. Paste in the whole shebang with SHIFT+INSERT.)

1. Download the correct library (as per 9 Dec 2011)
```

SOURCE_DIR="/tmp/motif"
TARGET_DIR="/usr/lib32"
DEB_URI="http://ftp.ubuntu.com/ubuntu/pool/multiverse/o/openmotif/libmotif4_2.3.3-5ubuntu1_i386.deb"
DEB_FN="$(basename ${DEB_URI})"
DEB_FP="${SOURCE_DIR}/${DEB_FN}"
mkdir -p ${SOURCE_DIR}
mkdir -p ${TARGET_DIR} # should be there already
pushd ${SOURCE_DIR}
wget -O ${DEB_FN} ${DEB_URI}
dpkg -x ${DEB_FN} ${SOURCE_DIR}
sudo cp -r ${SOURCE_DIR}/usr/lib/* ${TARGET_DIR}/

```

Then, link to the right place
```

MISSING_LIB_NAME="libXm.so.4.0.3"
MISSING_LIB_BASE="libXm.so"
TARGET_DIR="/usr/lib32"
SOURCE_DIR="/usr/lib"
find ${TARGET_DIR} -name "${MISSING_LIB_BASE}*" | xargs ls -al
sudo ln -s ${TARGET_DIR}/libXm.so.3.0.2 ${TARGET_DIR}/${MISSING_LIB_NAME}

```

Then ensure that file has correct permissions:
```

sudo chmod 644 /usr/lib32/libXm.so.3.0.2

```

Update the run-time linker cache:
```

sudo  ldconfig

```

Now check that all libs are good to go:
```

CLIENT_EXEC="/usr/lib/ICAClient/wfcmgr"
ldd ${CLIENT_EXEC}

```

This is all taken from the guide at
[https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")
with tiny modifications.

Please provide success/failure feedback as there are lots of buntu-users struggeling with this exact issue.

---

### Post by liziwizi on 2012-01-31
@Kaio

I just want to say that - after spending many many hours and more hours trying to fix this - your post got me the closest to a solution. 

Unbelievable how a professional company like citrix can release such a buggy product. 

Concerning your advice: first block went ok. Second block gave me an  error on the last statement that the file already existed. So I renamed  that file and did it again.
Third block didn't work because the version you mention (3.0.?)  is not on my system. 
And the Wfcmgr binary was located on a different location on my installation (/opt/...)  (i'm on ubuntu  11.1)
But now it starts and gives me the ssl 60 error (which i know how to fix).

Thanks again! I was getting desperate.

---

### Post by firep on 2012-02-26
> **liziwizi said:**
> @Kaio

I just want to say that - after spending many many hours and more hours trying to fix this - your post got me the closest to a solution. 

Unbelievable how a professional company like citrix can release such a buggy product. 

Concerning your advice: first block went ok. Second block gave me an  error on the last statement that the file already existed. So I renamed  that file and did it again.
Third block didn't work because the version you mention (3.0.?)  is not on my system. 
And the Wfcmgr binary was located on a different location on my installation (/opt/...)  (i'm on ubuntu  11.1)
But now it starts and gives me the ssl 60 error (which i know how to fix).

Thanks again! I was getting desperate.

HOW?  please tell me i also have ubuntu 11!!!! like you the post got me close until after the missing file thing!!!!

---

