---
title: "Windows corrupted NTFS external usb hdd, how to recover?"
date: 2010-11-13
forum: General Help
---

### Post by b_k_chu on 2010-11-13
I had a perfectly working Western Digital 250GB external usb hdd about 30 minutes ago.  It has about 130GB of data I spent 3 hours copying to it yesterday from my Ubuntu laptop.  Just to test it, I plugged it into an older Windows XP machine, and it seemed to work just fine.  Then I tried to do the "Safely Remove Hardware" thing.  It told me that it could not remove the external drive because another program was accessing it.  So okay, I just wait a minute or two.  Try again -- same thing.  Tried it several more times, waiting a minute or two between each try -- same thing.  Then suddenly a message pops up -- cannot write to drive.  I also get another error: drive is corrupt, run chkdsk utility.  Makes no sense.  I was accessing files from the drive from within Windows just fine minutes before.

So since it won't "unmount safely", I just unplug it (probably a mistake, but I didn't see that I had any other choice at the moment), then try mounting it using a LiveCD of Puppy Linux -- Puppy will not mount it, just gives an error but no details.

My Ubuntu laptop, however, is no longer usable -- after I copied the 130GB of files I wanted to save to my external hdd, I attempted an upgrade of Ubuntu.  It hosed.  I'm still on that Puppy Linux LiveCD right now as I type.

So then.  I KNOW this external hdd should be recoverable.  I didn't do anything to it except let Windows screw up its ability to be mounted/unmounted, somehow.  But I do not know how to go about trying to rescue it.  What are the tools I should use?  Is there something I can download somewhere that I can burn to a bootable CD or something that can fix a broken NTFS drive/partition?  It would almost have to be something bootable at this point since I don't know how to install anything new on Puppy.  Wasn't there an "Ultimate Linux Bootable Rescue CD" or something like that a while back?  I can't remember it's exact name now.

If worst comes to worst, I suppose I could always reformat the external hdd and then copy the files over to it again.  I still have all my files on my laptop's hard drive and Puppy can see them -- the Ubuntu upgrade I attempted did not overwrite all my stuff.  But....I would just rather avoid having to spend another 3 hours or more today doing that.  All my files are already on the external....I just want to fix it so that I can see them again.

Thanks.

---

### Post by arpanaut on 2010-11-13
> run chkdsk utility

Have you tried this from windows?
How did you partition the drive?
I have had issues with Windows not wanting to play nice with drives
formated to NTFS, FAT from linux.

try chkdsk, really nothing to lose except time if it fails.

---

### Post by Old_Grey_Wolf on 2010-11-13
This link may help: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=917431](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=917431)

---

### Post by coffeecat on 2010-11-13
> **arpanaut said:**
> try chkdsk, really nothing to lose except time if it fails.

+1. There is no alternative. There is no Linux tool that can repair a NTFS filesystem. The command line app ntfsfix merely schedules a chkdsk the next time the filesystem is used in Windows.

Actually there is one alternative. I've not used it myself but there is a mini-XP with chkdsk on the Hiren's boot CD, except that I could not find a download link for this. Besides, you already have Windows XP even if it was responsible for the problem in the first place.

---

### Post by b_k_chu on 2010-11-13
woo!  i'm a real winner today!  (total sarcasm)

just for kicks i tried the 
```
# ntfs-3g /dev/sdb1 /mnt/sdb1 -o force
```route on Puppy, got an error message basically telling me, "Use Chkdsk To Fix It."

so ok, next on windows i
```
chkdsk g: /f
```and Windows sez:
> Unable to determine volume version and state.  CHKDSK aborted.alrighty then!  windows borked it and then tells me, "lol i dunno how to fix it".  this is really pathetic but i'm laughing!

looks like Project Format External HDD to FAT32 shall commence!

but thanks for the pointers, guys.  at least it helped me determine that i have a total meltdown on my hands. :3

---

### Post by Old_Grey_Wolf on 2010-11-13
Edit: sorry, I just read the part about using the Puppy Live CD. So this probably will not work.

Try this by adding the mkdir command first

```
sudo mkdir /media/external

```

and then enter

```
sudo ntfs-3g /dev/sdb1 /media/external -o force
```

---

### Post by trellis2 on 2010-11-13
If you have a working Windows 7 machine you can repair it with its disk utility. And it's gonna take a long time but it usually fixes the problem.
I repaired my external 1TB Simpletech drive with a windows 7 virtual machine. If anybody knows of another way let me know. 
[http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors]("http://windows.microsoft.com/en-US/windows-vista/Check-your-hard-disk-for-errors")

---

### Post by Old_Grey_Wolf on 2010-11-13
b_k_chu,

I guess you are busy formatting the disk. I'm glad you kept your sense of humor. Sometimes when you put Linux and Windows in the same playground sandbox they don't play nicely together. :)

I have a persistent 4GB USB thumb drive with Ubuntu on it just for situations like this. Currently it has 10.04 LTS on it.

---

### Post by b_k_chu on 2010-11-13
@trellis2:
sorry, i have no windows7 available to me.

@Old_Gray_Wolf
actually, no....because i'm stubborn, i'm currently using TestDisk off of the Ultimate Boot CD to run a deep scan on it looking for broken partitions.  if this fails then yeah, i probably will metaphorically choke down that brick of cold, frozen spinach and reformat the external into FAT32 and copy over everything again.

by the way, it wouldn't matter what mount point you used for the ntfs-3g command, so long as it was an existing directory.  with Puppy /mnt/sdb1 just happened to be there already.

(talking to myself here) woo, i've been on all kinds of OSes today....currently i'm on PartedMagic's OS while TestDisk runs....it looks pretty nice.  nicer than my ubuntu did, to be honest. :3

---

### Post by oldfred on 2010-11-13
You can download a Vista or & repair CD. From that you can run chkdsk.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Linux typically does not want to mount a NTFS drive that has the chkdsk flag set as then you may further damage the drive and chkdsk will not repair it. The force is as a last resort to let you copy your data to another device.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

---

### Post by Old_Grey_Wolf on 2010-11-13
> **b_k_chu said:**
> @Old_Gray_Wolf
actually, no....because i'm stubborn, i'm currently using TestDisk off of the Ultimate Boot CD to run a deep scan on it looking for broken partitions.  if this fails then yeah, i probably will metaphorically choke down that brick of cold, frozen spinach and reformat the external into FAT32 and copy over everything again.

I'm glad you didn't give up and reformat the disk. I was thinking that you could also try to fix the failed Ubuntu upgrade; however, I'm guessing that you already tried that. :)

"choke down that brick of cold, frozen spinach" Unfortunately I got a visual image of that in my head. Gaaaag. 
:lolflag:

> **b_k_chu said:**
> by the way, it wouldn't matter what mount point you used for the ntfs-3g command, so long as it was an existing directory.  with Puppy /mnt/sdb1 just happened to be there already.

That was part of the reason for the **edit**. I couldn't remember if Puppy used sudo, and whether it used /media or /mnt. I haven't used Puppy in a long time. With the persistent Ubuntu USB thumb drive, I can do things that can't be done from a Live CD. :)

I wish you well solving this problem.

And, keep your sense of humor. It may be the only thing keeping you sane. :)

---

### Post by b_k_chu on 2010-11-13
@oldfred
i already ran chkdsk and it didn't work.  i also ran TestDisk and it flopped too, even on the deep scan.  which tells me that windows really farked it up som'n good.

@Old_Gray_Wolf
well since TestDisk failed to rescue, i did reformat the disk.  but that wasn't any good because Puppy and PartedMagic file managers could not handle copying over 20,000 files or so with all the crazy characters i have in my filenames.

so i cloned it.  CopyWipe 1.14 off the Ultimate Boot CD backed up everything.  yeeha.

anyhow, i'm marking this thread solved even though i didn't really find a "fix".  i just found an answer:

1. with NTFS external usb hard drives, if you suddenly get messages from windows saying something like "Can't write to $MFT" and the drive quits working,

2. running chkdsk :*drive* /f fails to do anything and chkdsk just aborts,

3. you try to force it to mount in linux with ntfs-3g *device mountpoint *-o force and you get a message like ```
Record 0 has no FILE magic (0x*address*)
Failed to load $MFT: Input/Output error
Failed to mount '*device*': Input/Output error
NTFS is either inconsistent, or you have hardware faults, or you have a SoftRAID/FakeRAID hardware ...etc etc...
```then 4.  it's Game Over.  your hard drive has just been turned into a brick.

5. have fun reformatting.


p.s. thanks for hanging with me on this, everyone who responded.  at least i felt like i had some company through these dark, lonely hours. :3

---

### Post by rickyrockrat on 2012-10-17
Yes I know it is 2 years old. I'm posting for reference.

Get scrounge-ntfs - it won't fix the drive, but it will recover files from a bad drive - one that won't mount. I had to fix the code so it would see a larger drive. Here is the file I modified - just had to use a longer variable for the 2T drive.
[http://thewalter.net/stef/software/scrounge/](http://thewalter.net/stef/software/scrounge/)
This should replace the main.c file.

```
/* 
 * AUTHOR
 * Stef Walter
 *
 * LICENSE
 * This software is in the public domain.
 *
 * The software is provided "as is", without warranty of any kind,
 * express or implied, including but not limited to the warranties
 * of merchantability, fitness for a particular purpose, and
 * noninfringement. In no event shall the author(s) be liable for any
 * claim, damages, or other liability, whether in an action of
 * contract, tort, or otherwise, arising from, out of, or in connection
 * with the software or the use or other dealings in the software.
 * 
 * SUPPORT
 * Send bug reports to: <stef@memberwebs.com>
 */

#include "usuals.h"
#include "scrounge.h"
#include "compat.h"

#ifdef _WIN32

const char kPrintHelp[]       = "\
usage: scrounge -l                                                   \n\
  List all drive partition information.                              \n\
                                                                     \n\
usage: scrounge [-d drive] -s                                        \n\
  Search drive for NTFS partitions.                                  \n\
                                                                     \n\
usage: scrounge [-d drive] [-m mftoffset] [-c clustersize] [-o outdir] start end  \n\
  Scrounge data from a partition                                     \n\
  -d         Drive number                                            \n\
  -m         Offset to mft (in sectors)                              \n\
  -c         Cluster size (in sectors, default of 8)                 \n\
  -o         Directory to put scrounged files in                     \n\
  start      First sector of partition                               \n\
  end        Last sector of partition                                \n\
                                                                     \n\
";

#else /* Not WIN32 */

const char kPrintHelp[]       = "\
usage: scrounge -l disk                                              \n\
  List all drive partition information.                              \n\
                                                                     \n\
usage: scrounge -s disk                                              \n\
  Search drive for NTFS partitions.                                  \n\
                                                                     \n\
usage: scrounge [-m mftoffset] [-c clustersize] [-o outdir] disk start end  \n\
  Scrounge data from a partition                                     \n\
  -m         Offset to mft (in sectors)                              \n\
  -c         Cluster size (in sectors, default of 8)                 \n\
  -o         Directory to put scrounged files in                     \n\
  disk       The raw disk partitios (ie: /dev/hda)                   \n\
  start      First sector of partition                               \n\
  end        Last sector of partition                                \n\
                                                                     \n\
";

#endif

#define MODE_SCROUNGE 1
#define MODE_LIST     2
#define MODE_SEARCH   3 

/* Forward decls */
void usage();

#ifdef _DEBUG
bool g_verifyMode = false;
#endif

int main(int argc, char* argv[])
{
  int ch = 0;
  unsigned long temp = 0;
  int mode = 0;
  int raw = 0;
  partitioninfo pi;
  char driveName[MAX_PATH + 1];
#ifdef _WIN32
  int drive = 0;
#endif

  memset(&pi, 0, sizeof(pi));

  /* TODO: We need to be able to autodetect the cluster size */
  pi.cluster = 8;

#ifdef _WIN32
  while((ch = getopt(argc, argv, "c:d:hlm:o:sv")) != -1)
#else
  while((ch = getopt(argc, argv, "c:hlm:o:sv")) != -1)
#endif
  {
    switch(ch)
    {

    /* cluster size */
    case 'c':
      {
        temp = atol(optarg);
        
        /* TODO: Check this range */
        if(temp <= 0 || temp > 128)
          errx(2, "invalid cluster size (must be between 1 and 128)");

        pi.cluster = temp;
        mode = MODE_SCROUNGE;
      }
      break;

#ifdef _WIN32
    /* drive number */
    case 'd':
      {
        temp = atol(optarg);

        /* TODO: Check this range */
        if(temp < 0 || temp > 128)
          errx(2, "invalid drive number (must be between 0 and 128)");

        drive = temp;
      }
      break;
#endif

    /* list mode */
    case 'l':
      {
        if(mode == MODE_SCROUNGE)
          errx(2, "invalid -l argument in scrounge mode");

        mode = MODE_LIST;
      }
      break;

    /* mft offset */
    case 'm':
      {
        temp = atol(optarg);

        /* TODO: Check this range */
        if(temp < 0)
          errx(2, "invalid mft offset (must be positive)");

        pi.mft = temp;
        mode = MODE_SCROUNGE;
      }
      break;

    /* output directory */
    case 'o':
      if(chdir(optarg) == -1)
        err(2, "couldn't change to output directory");
      break;

    /* search mode */
    case 's':
      {
        if(mode == MODE_SCROUNGE)
          errx(2, "invalid -s argument in scrounge mode");

        mode = MODE_SEARCH;
      }
      break;

#ifdef _DEBUG
    case 'v':
      g_verifyMode = true;
      break;
#endif

    /* help mode */
    case '?':
    case 'h':
    default:
      usage();
      break;
    };

    if(mode != MODE_SCROUNGE && mode != 0)
      break;
  }

  argc -= optind;
  argv += optind;

#ifdef _WIN32
  /* Under windows we format the drive number */
  makeDriveName(driveName, drive);

#else
  /* Now when not under Windows, it's the drive name */
  if(argc < 1)
    errx(2, "must specify drive name");

  strncpy(driveName, argv[0], MAX_PATH);
  driveName[MAX_PATH] = 0;

  argv++;
  argc--;
#endif


  if(mode == MODE_SCROUNGE || mode == 0)
  {
    /* Get the sectors */

    if(argc < 2)
      errx(2, "must specify start and end sector of partition");

    if(argc > 2)
      warnx("ignoring extra arguments");

    temp = atol(argv[0]);
    if(temp < 0)
      errx(2, "invalid start sector (must be positive)");

    pi.first = temp;

    temp = atol(argv[1]);
    if(temp < 0 || temp <= pi.first)
      errx(2, "invalid end sector (must be positive and greater than first)");

    pi.end = temp;

    /* Open the device */
    pi.device = open(driveName, O_BINARY | O_RDONLY | OPEN_LARGE_OPTS);
    if(pi.device == -1)
      err(1, "couldn't open drive: %s", driveName);

    /* Use mft type search */
    if(pi.mft != 0)
    {
      scroungeUsingMFT(&pi);
    }

    /* Otherwise it's a raw search */
    else
    {
      warnx("Scrounging via raw search. Directory info will be discarded.");
      scroungeUsingRaw(&pi);
    }
  }

  else
  {
    if(argc > 0)
      warnx("ignoring extra arguments");

    /* List partition and drive info */
    if(mode == MODE_LIST)
#ifdef _WIN32
      scroungeList();
#else
      scroungeListDrive(driveName);
#endif

    /* Search for NTFS partitions */
    if(mode == MODE_SEARCH)
      scroungeSearch(&pi);
  }

  return 0;
}

void usage()
{
  fprintf(stderr, "%s", kPrintHelp);
  exit(2);
}
```

---

