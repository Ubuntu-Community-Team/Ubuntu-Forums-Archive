---
title: "Help with for loop with find"
date: 2010-05-20
forum: General Help
---

### Post by domzz on 2010-05-20
```
#!/bin/sh --
# The directory name that holds your movies.
DIR="/home/domz/torrents"
# Creating the subdirectory names that hold the result and the backup.
#for NEW in swf backup; do
 #mkdir "${DIR}/${NEW}" || { echo "Could not create ${DIR}/${NEW}, exiting."; exit 1; }
#done
# Start looping over files, tell what we do and log any output to screen and log.
for MPEG in `find ${DIR} -iname "*mp4"` ; do echo "Starting ${MPEG}"

	HandBrakeCLI -i "${MPEG}" -o "${DIR}/${MPEG%.mpg}.m4v"  -e x264 -q 0.589999973773956 -a 1 -E faac -B 128 -R 48 -6 dpl2 -f mp4 -X 480 -m -x level=30:cabac=0:ref=2:mixed-refs:analyse=all:me=umh:no-fast-pskip=1
 # If ffmpeg exited OK, then say it and move the original to the backup directory.
 if [ $? -eq 0 ]; then
  echo "Completed ${MPEG%.mpg}.m4v"; #mv "${MPEG}" ${DIR}/backup || { echo "Could not move ${MPEG}, exiting."; exit 1; }
 else
  # If ffmpeg failed, then say so and exit loop.
  echo "FAILED converting ${MPEG}, exiting."; exit 1; 
 fi
done # End of file loop
# Exit.
exit 0
```


The output is just this:
```
Starting /home/domz/torrents/tester
[09:17:30] hb_init: checking cpu count
[09:17:30] hb_init: starting libhb thread
HandBrake 0.9.4 (2009112300) - Linux x86_64 - http://handbrake.fr
4 CPUs detected
Opening /home/domz/torrents/tester...
[09:17:30] hb_scan: path=/home/domz/torrents/tester, title_index=1
[09:17:30] scan: trying to open with libdvdread
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat /home/domz/torrents/tester
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[09:17:30] dvd: not a dvd - trying as a stream/file instead
[09:17:30] hb_stream_open: open /home/domz/torrents/tester failed
[09:17:30] scan: unrecognized file type
[09:17:30] libhb: scan thread found 0 valid title(s)
No title found.
HandBrake has exited.
Completed /home/domz/torrents/tester.m4v
Starting directory/how-to-beat-friends-wii.mp4
[09:17:30] hb_init: checking cpu count
[09:17:30] hb_init: starting libhb thread
HandBrake 0.9.4 (2009112300) - Linux x86_64 - http://handbrake.fr
4 CPUs detected
Opening directory/how-to-beat-friends-wii.mp4...
[09:17:30] hb_scan: path=directory/how-to-beat-friends-wii.mp4, title_index=1
[09:17:30] scan: trying to open with libdvdread
libdvdnav: Using dvdnav version 4.1.3
libdvdread: Encrypted DVD support unavailable.
libdvdread: Can't stat directory/how-to-beat-friends-wii.mp4
No such file or directory
libdvdnav: vm: failed to open/read the DVD
[09:17:30] dvd: not a dvd - trying as a stream/file instead
[09:17:30] hb_stream_open: open directory/how-to-beat-friends-wii.mp4 failed
[09:17:30] scan: unrecognized file type
[09:17:30] libhb: scan thread found 0 valid title(s)
No title found.
HandBrake has exited.
Completed directory/how-to-beat-friends-wii.mp4.m4v  
```

---

