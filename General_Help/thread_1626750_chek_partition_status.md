---
title: "chek partition status"
date: 2010-11-20
forum: General Help
---

### Post by taxidimu on 2010-11-20
Ubuntu server, no GUI installed; two partitions: OS and user.
How can I check the status of the user partition? E.g. Free space, directory, etc

---

### Post by acrazyplayer on 2010-11-20
the command "df" is your friend, man it or help it to learn more

---

### Post by dcstar on 2010-11-20
> **taxidimu said:**
> Ubuntu server, no GUI installed; two partitions: OS and user.
How can I check the status of the user partition? E.g. Free space, directory, etc

Copy this script into your /usr/local/bin folder, make it executable and call it "dfspace":
```
#!/bin/sh -

# dfspace - d(isk) f(ree) space
#
# Calculate available disk space in all mounted filesystems
# with the exception of psuedo file systems such as /proc and /dev/fd.
#
# Alternately, report on filesystems/devices specified on cmd-line.
#   Filesystem may be 1K bytes/block, but, df uses 512 bytes/block.
#

# get free and allocated space.
df -k $* 2>/dev/null | awk '
BEGIN {  AVAIL=0; TOTAL=0 }
{
	if ( $6 != "/proc" && $6 != "/dev/fd" && $1 != "Filesystem" )
	{
#print $1 $2 $3 $4 $5 $6
		AVAIL += $4
		TOTAL += $2
		while (length($6)<28) $6 = $6 " "
		printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",$6, $4 / 1024, $2 / 1024, $4 * 100 / $2 )

	}
}
END { printf("-------------------------------------------------------------------------------\n")
printf("%s: %#7.2f MB of %#7.2f MB available (%#6.2f%%)\n",
	"            Total           ", AVAIL / 1024, TOTAL / 1024, AVAIL * 100 / TOTAL)

}'

# end of disk space calculation.
```

---

