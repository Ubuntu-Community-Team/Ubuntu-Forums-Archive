---
title: "gphotofs: Protocol error."
date: 2010-07-25
forum: General Help
---

### Post by prodigy_ on 2010-07-25
I have a Kodak V1073 digital camera. I don't have a memory card for it, so I just connect it via USB and transfer photos in small batches. Obviously, this works in Windows, but I want to be able to do the same on my Ubuntu laptop.

So I intalled gphotofs, created a directory called /media/Kodak and mounted my camera:```

sudo mkdir /media/Kodak
sudo chown 1000:1000 /media/Kodak
gphotofs /media/Kodak
```

And everything seemed to work fine but: ```
$ ls -la /media/Kodak/
ls: reading directory /media/Kodak/: Protocol error
total 0
```

Any ideas?

---

[edit/SOLVED]: Sorry, seems that the camera turned off while I was preparing things. :-) Now everything works.

If anyone's interested, here's a sample script: ```
#!/bin/sh

printf "\n%s" "Preparing to import photos... "

if	[ ! -d /media/Camera ]; then
	sudo mkdir -p /media/Camera
	sudo chown $(id -u):$(id -u) /media/Camera
fi

fusermount -u /media/Camera >/dev/null 2>&1

test -d ~/Pictures/Photos || mkdir -p ~/Pictures/Photos

printf "%b" "done! \nAccessing the camera... "
gphotofs /media/Camera

v_TryCounter="0"

while	! ls -la /media/Camera >/dev/null 2>&1 && [ "$v_TryCounter" -lt "5" ]
do
	sleep 1
	v_TryCounter="$(expr $v_TryCounter + 1)"
done

if	! ls -la /media/Camera >/dev/null 2>&1; then
	fusermount -u /media/Camera >/dev/null 2>&1
	printf "%s\n\n" "ERROR! Cannot access the camera! "
	sleep 10
	exit 1
fi

printf "%b" "done! \nGenerating the list of photos... "
v_FileList="$(find /media/Camera -type f -print0|xargs -0 file|grep 'JPEG'|cut -d':' -f 1)"
printf "%b" "done! \nMoving the photos... "

for i in $v_FileList
do
	mv -f $i ~/Pictures/Photos
done

printf "%b\n\n" "done! \nAll done! "

fusermount -u /media/Camera
nautilus ~/Pictures/Photos
```

---

