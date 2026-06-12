---
title: "Using Ubuntu to Recover Google Chrome OS on CR-48"
date: 2010-12-19
forum: General Help
---

### Post by HappinessNow on 2010-12-19
So I accidentally locked my self out of my CR-48, I now need to recover chrome OS using Ubuntu (can only recover using Linux or Mac at this point)

So I have the following notice:

[IMG]http://www.google.com/help/hc/images/chromeos_ponyRecovery.png[/IMG]

from the Google Chrome OS recovery page:

> If your Cr-48 notebook fails to boot, you may see the following screen asking you to recover the Chrome notebook. To do so, follow these steps to create a bootable USB flash drive and recover your notebook.

[IMG]http://www.google.com/help/hc/images/chromeos_ponyRecovery.png[/IMG]

Before starting this process, you'll need the following:
A Mac or Linux computer with admin rights (Windows instructions are coming soon.)
A 4 GB or larger USB Flash drive that you don't mind clearing.

Step 1: Create a Chrome OS Recovery USB Flash drive

You can build a Chrome OS recovery USB drive either by using the Chrome OS Recovery tool or by manually building an image.

Using the Recovery tool

Click this link to download the Chrome OS Recovery Tool for Linux: [https://dl.google.com/dl/edgedl/chromeos/recovery/linux_recovery.sh](https://dl.google.com/dl/edgedl/chromeos/recovery/linux_recovery.sh)

Run the script with root privileges. Follow the instructions from the tool to complete building your OS. If this fails, try manually building an image below.

Manually building an image

Click this link to download the image: [https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel](https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel) 
Extract the .bin file from the .zip you just downloaded (e.g. ChromeOS--recovery.bin ).
Insert a USB Flash drive into your Linux computer's USB port.
Open a terminal window and enter the following command: $ sudo fdisk -l
You should then see the drive name, such as /dev/sdc.

Enter and edit the following command: Run: $ sudo dd if=chromeos-recovery.bin of=/dev/sdX
Replace /dev/sdX with the name of your USB device from step 4
Replace chromeos-recovery.bin with the name of the file you extracted from step 2

CAUTION: Entering the wrong drive name in this step can result in both serious loss of information and system damage.

Step 2: Recover your Chrome notebook from the USB Flash drive

When the "Chrome OS is missing or damaged" screen appears, insert the USB Flash drive you created into the USB port on the right side of your notebook.
Wait for the notebook to boot up from the Flash drive.
Follow the instructions that appear on the screen.
On successful reinstall, the system will automatically restart.
Remove the USB Flash drive from your notebook.
You should now be able to start and use your Chrome notebook as normal.

So I have elected to use Ubuntu to recover my Chrome OS, and I have an 8gb flash drive ready.

I downloaded the recovery tool and have it open in gedit but I have no idea what to do with it, the instructions are quite confusing. So I decided it Would be less complicated to manually build an image at this point...

Also it says I need root privileges so I am currently logged in as root

preceding to Manually build an image following these instructions:

> Click this link to download the image: [https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel](https://dl.google.com/dl/chromeos/recovery/latest_mario_beta_channel) 
Extract the .bin file from the .zip you just downloaded (e.g. ChromeOS--recovery.bin ).
Insert a USB Flash drive into your Linux computer's USB port.
Open a terminal window and enter the following command: $ sudo fdisk -l
You should then see the drive name, such as /dev/sdc.

Enter and edit the following command: Run: $ sudo dd if=chromeos-recovery.bin of=/dev/sdX
Replace /dev/sdX with the name of your USB device from step 4
Replace chromeos-recovery.bin with the name of the file you extracted from step 2

Ok so I 

1. downloaded the latest_mario_beta_channel
2. Extracted the .bin file from the .zip (renamed it chromeos-recovery.bin)
3. Inserted a USB Flash drive into my Ubuntu computer
4. saw the drive name: /dev/sdb1
5. ran the command in the terminal:
sudo dd if=chromeos-recovery-bin of=/dev/sdb1

I get the following output:

dd: opening `chromeos-recovery.bin': No such file or directory

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178850&d=1292765528[/IMG]

here is where the chromeos-recovery.bin file is:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178849&d=1292765528[/IMG]

Any help at this point would be greatly appreciated.

below is the recovery tool that I found too confusing:

```
#!/bin/sh
#
# Copyright (c) 2010 The Chromium OS Authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.
#
# This attempts to guide linux users through the process of putting a recovery
# image onto a removeable USB drive.
#
# We may not need root privileges if we have the right permissions.
#
set -eu

##############################################################################
# Configuration goes here

# Where should we do our work? Use 'WORKDIR=' to make a temporary directory,
# but using a persistent location may let us resume interrupted downloads or
# run again without needing to download a second time.
WORKDIR=${WORKDIR:-/tmp/tmp.crosrec}

# Where do we look for the config file? Note that we can override this by just
# specifying the config file URL on the command line.
CONFIGURL="${1:-https://dl.google.com/dl/edgedl/chromeos/recovery/recovery.conf}"

# Device to put this stuff on, perhaps the user knows best?
DEVICE="${DEVICE:-}"

# What version is this script? It must match the 'recovery_tool_version=' value
# in the config file that we'll download.
MYVERSION='0.9.2'


##############################################################################
# Some temporary filenames
debug='debug.log'
tmpfile='tmp.txt'
config='config.txt'
version='version.txt'

##############################################################################
# Various warning messages

DEBUG() {
  echo "DEBUG: $@" >>"$debug"
}

prompt() {
  # builtin echo may not grok '-n'. We should always have /bin/echo, right?
  /bin/echo -n "$@"
}

warn() {
  echo "$@" 1>&2
}

quit() {
  warn "quitting..."
  exit 1
}

fatal() {
  warn "ERROR: $@"
  exit 1
}

ufatal() {
  warn "
ERROR: $@

You may need to run this program as a different user. If that doesn't help, try
using a different computer, or ask a knowledgeable friend for help.

"
  exit 1
}

gfatal() {
  warn "
ERROR: $@

You may need to run this program as a different user. If that doesn't help, it
may be a networking problem or a problem with the images provided by Google.
You might want to check to see if there is a newer version of this tool
available, or if someone else has already reported a problem.

If all else fails, you could try using a different computer, or ask a
knowledgeable friend for help.

"
  exit 1
}

##############################################################################
# Identify the external utilities that we MUST have available.
#
# I'd like to keep the set of external *NIX commands to an absolute minimum,
# but I have to balance that against producing mysterious errors because the
# shell can't always do everything. Let's make sure that these utilities are
# all in our $PATH, or die with an error.
#
# This also sets the following global variables to select alternative utilities
# when there is more than one equivalent tool available:
#
#   FETCH          = name of utility used to download files from the web
#   CHECK          = command to invoke to generate checksums on a file
#   CHECKTYPE      = type of checksum generated
#   DISKUTIL       = set if we have 'diskutil' (for Macs)
#
require_utils() {
  local external
  local errors
  local tool
  local tmp

  external='cat cut dd grep ls mkdir mount readlink sed sync umount unzip wc'
  if [ -z "$WORKDIR" ]; then
    external="$external mktemp"
  fi
  errors=

  for tool in $external ; do
    if ! type "$tool" >/dev/null 2>&1 ; then
      warn "ERROR: need \"$tool\""
      errors=yes
    fi
  done

  # We also need to a way to fetch files from teh internets. Note that the args
  # are different depending on which utility we find. We'll use two variants,
  # one to fetch fresh every time and one to try again from where we left off.
  FETCH=
  if [ -z "$FETCH" ] && tmp=$(type curl 2>/dev/null) ; then
    FETCH=curl
  fi
  if [ -z "$FETCH" ] && tmp=$(type wget 2>/dev/null) ; then
    FETCH=wget
  fi
  if [ -z "$FETCH" ]; then
    warn "ERROR: need \"curl\" or \"wget\""
    errors=yes
  fi

  # Once we've fetched a file we need to compute its checksum. There are
  # multiple possiblities here too.
  CHECK=
  if [ -z "$CHECK" ] && tmp=$(type md5sum 2>/dev/null) ; then
    CHECK="md5sum"
    CHECKTYPE="md5"
  fi
  if [ -z "$CHECK" ] && tmp=$(type sha1sum 2>/dev/null) ; then
    CHECK="sha1sum"
    CHECKTYPE="sha1"
  fi
  if [ -z "$CHECK" ] && tmp=$(type openssl 2>/dev/null) ; then
    CHECK="openssl"
    CHECKTYPE="md5"
  fi
  if [ -z "$CHECK" ]; then
    warn "ERROR: need \"md5sum\" or \"sha1sum\" or \"openssl\""
    errors=yes
  fi

  # This utility is on Macs, so use it if we find it.
  DISKUTIL=
  if type diskutil >/dev/null 2>&1; then
    DISKUTIL=diskutil
  fi

  if [ -n "$errors" ]; then
    ufatal "Some required utilities are missing."
  fi
}

# This retrieves a URL and stores it locally. It uses the global variable
# 'FETCH' to determine the utility (and args) to invoke.
# Args:  URL FILENAME [RESUME]
fetch_url() {
  local url
  local filename
  local resume
  local err

  url="$1"
  filename="$2"
  resume="${3:-}"

  DEBUG "FETCH=($FETCH) url=($url) filename=($filename) resume=($resume)"

  if [ "$FETCH" = "curl" ]; then
    if [ -z "$resume" ]; then
      # quietly fetch a new copy each time
      rm -f "$filename"
      curl -L -f -s -S -o "$filename" "$url"
    else
      # continue where we left off, if possible
      curl -L -f -C - -o "$filename" "$url"
      # If you give curl the '-C -' option but the file you want is already
      # complete and the server doesn't report the total size correctly, it
      # will report an error instead of just doing nothing. We'll try to work
      # around that.
      err=$?
      if [ "$err" = "18" ]; then
        warn "Ignoring spurious complaint"
        true
      fi
    fi
  elif [ "$FETCH" = "wget" ]; then
    if [ -z "$resume" ]; then
      # quietly fetch a new copy each time
      rm -f "$filename"
      wget -nv -q -O "$filename" "$url"
    else
      # continue where we left off, if possible
      wget -c -O "$filename" "$url"
    fi
  fi
}

# This returns a checksum on a file. It uses the global variable 'CHECK' to
# determine the utility (and args) to invoke.
# Args:  FILENAME
compute_checksum() {
  local filename

  filename="$1"

  DEBUG "CHECK=($CHECK) CHECKTYPE=($CHECKTYPE)"

  if [ "$CHECK" = "openssl" ]; then
    openssl md5 < "$filename"
  else
    $CHECK "$zipfile" | cut -d' ' -f1
  fi
}


##############################################################################
# Helper functions to handle the config file and image zipfile.

# Each paragraph in the config file should describe a new image. Let's make
# sure it follows all the rules. This scans the config file and returns success
# if it looks valid. As a side-effect, it lists the line numbers of the start
# and end of each stanza in the global variables 'start_lines' and 'end_lines'
# and saves the total number of images in the global variable 'num_images'.
good_config() {
  local line
  local key
  local val
  local name
  local file
  local zipfilesize
  local filesize
  local url
  local md5
  local sha1
  local skipping
  local errors
  local count
  local line_num

  name=
  file=
  zipfilesize=
  filesize=
  url=
  md5=
  sha1=
  skipping=yes
  errors=
  count=0
  line_num=0

  # global
  start_lines=
  end_lines=

  while read line; do
    line_num=$(( line_num + 1 ))

    # We might have some empty lines before the first stanza. Skip them.
    if [ -n "$skipping" ] && [ -z "$line" ]; then
      continue
    fi

    # Got something...
    if [ -n "$line" ]; then
      key=${line%=*}
      val=${line#*=}
      if [ -z "$key" ] || [ -z "$val" ] || [ "$key=$val" != "$line" ]; then
        DEBUG "ignoring $line"
        continue
      fi

      # right, looks good
      if [ -n "$skipping" ]; then
        skipping=
        start_lines="$start_lines $line_num"
      fi

      case $key in
        name)
          if [ -n "$name" ]; then
            DEBUG "duplicate $key"
            errors=yes
          fi
          name="$val"
          ;;
        file)
          if [ -n "$file" ]; then
            DEBUG "duplicate $key"
            errors=yes
          fi
          file="$val"
          ;;
        zipfilesize)
          if [ -n "$zipfilesize" ]; then
            DEBUG "duplicate $key"
            errors=yes
          fi
          zipfilesize="$val"
          ;;
        filesize)
          if [ -n "$filesize" ]; then
            DEBUG "duplicate $key"
            errors=yes
          fi
          filesize="$val"
          ;;
        url)
          url="$val"
          ;;
        md5)
          md5="$val"
          ;;
        sha1)
          sha1="$val"
          ;;
      esac
    else
      # Between paragraphs. Time to check what we've found so far.
      end_lines="$end_lines $line_num"
      count=$(( count + 1))

      if [ -z "$name" ]; then
        DEBUG "image $count is missing name"
        errors=yes
      fi
      if [ -z "$file" ]; then
        DEBUG "image $count is missing file"
        errors=yes
      fi
      if [ -z "$zipfilesize" ]; then
        DEBUG "image $count is missing zipfilesize"
        errors=yes
      fi
      if [ -z "$filesize" ]; then
        DEBUG "image $count is missing filesize"
        errors=yes
      fi
      if [ -z "$url" ]; then
        DEBUG "image $count is missing url"
        errors=yes
      fi
      if [ "$CHECKTYPE" = "md5" ] && [ -z "$md5" ]; then
        DEBUG "image $count is missing required md5"
        errors=yes
      fi
      if [ "$CHECKTYPE" = "sha1" ] && [ -z "$sha1" ]; then
        DEBUG "image $count is missing required sha1"
        errors=yes
      fi

      # Prepare for next stanza
      name=
      file=
      zipfilesize=
      filesize=
      url=
      md5=
      sha1=
      skipping=yes
    fi
  done < "$config"

  DEBUG "$count images found"
  num_images="$count"

  DEBUG "start_lines=($start_lines)"
  DEBUG "end_lines=($end_lines)"

  # return error status
  [ "$count" != "0" ] && [ -z "$errors" ]
}


# Make the user pick an image to download. On success, it sets the global
# variable 'user_choice' to the selected image number.
choose_image() {
  local show
  local count
  local line
  local num

  show=yes
  while true; do
    if [ -n "$show" ]; then
      echo
      if [ "$num_images" -gt 1 ]; then
        echo "There are $num_images recovery images to choose from:"
      else
        echo "There is $num_images recovery image to choose from:"
      fi
      echo
      count=0
      echo "0 - <quit>"
      # NOTE: making assumptions about the order of lines in each stanza!
      while read line; do
        if echo "$line" | grep -q '^name='; then
          echo
          count=$(( count + 1 ))
          echo "$line" | sed "s/name=/$count - /"
        elif echo "$line" | grep -q '^channel='; then
          echo "$line" | sed 's/channel=/      channel:  /'
        elif echo "$line" | grep -q '^hwid='; then
          echo "$line" | sed 's/hwid=/      model:    /'
        fi
      done < "$config"
      echo
      show=
    fi
    prompt "Please select a recovery image to download: "
    read num
    if [ -z "$num" ] || [ "$num" = "?" ]; then
      show=yes
    elif echo "$num" | grep -q '[^0-9]'; then
      echo "Sorry, I didn't understand that."
    else
      if [ "$num" -lt "0" ] || [ "$num" -gt "$num_images" ]; then
        echo "That's not one of the choices."
      elif [ "$num" -eq 0 ]; then
        quit
      else
        break;
      fi
    fi
  done
  echo

  # global
  user_choice="$num"
}

# Fetch and verify the user's chosen image. On success, it sets the global
# variable 'image_file' to indicate the local name of the unpacked binary that
# should be written to the USB drive.
fetch_image() {
  local start
  local end
  local line
  local key
  local val
  local file
  local zipfilesize
  local filesize
  local url
  local md5
  local sha1
  local line_num
  local zipfile
  local err
  local sum

  file=
  zipfilesize=
  filesize=
  url=
  md5=
  sha1=
  line_num="0"

  # Convert image number to line numbers within config file.
  start=$(echo $start_lines | cut -d' ' -f$1)
  end=$(echo $end_lines | cut -d' ' -f$1)

  while read line; do
    # Skip to the start of the desired stanza
    line_num=$(( line_num + 1 ))
    if [ "$line_num" -lt "$start" ] || [ "$line_num" -ge "$end" ]; then
      continue;
    fi

    # Process the stanza.
    if [ -n "$line" ]; then
      key=${line%=*}
      val=${line#*=}
      if [ -z "$key" ] || [ -z "$val" ] || [ "$key=$val" != "$line" ]; then
        DEBUG "ignoring $line"
        continue
      fi

      case $key in
        # The descriptive stuff we'll just save for later.
        file)
          file="$val"
          ;;
        zipfilesize)
          zipfilesize="$val"
          ;;
        filesize)
          filesize="$val"
          ;;
        md5)
          md5="$val"
          ;;
        sha1)
          sha1="$val"
          ;;
        url)
          # Try to download each url until one works.
          if [ -n "$url" ]; then
            # We've already got one (it's very nice).
            continue;
          fi
          warn "Downloading image zipfile from $val"
          warn ""
          zipfile=${val##*/}
          if fetch_url "$val" "$zipfile" "resumeok"; then
            # Got it.
            url="$val"
          fi
          ;;
      esac
    fi
  done < "$config"

  if [ -z "$url" ]; then
    DEBUG "couldn't fetch zipfile"
    return 1
  fi

  # Verify the zipfile
  if ! ls -l "$zipfile" | grep -q "$zipfilesize"; then
    DEBUG "zipfilesize is wrong"
    return 1
  fi
  sum=$(compute_checksum "$zipfile")
  DEBUG "checksum is $sum"
  if [ "$CHECKTYPE" = "md5" ] && [ "$sum" != "$md5" ]; then
    DEBUG "wrong $CHECK"
    return 1
  elif [ "$CHECKTYPE" = "sha1" ] && [ "$sum" != "$sha1" ]; then
    DEBUG "wrong $CHECK"
    return 1
  fi

  # Unpack the file
  warn "Unpacking the zipfile"
  rm -f "$file"
  if ! unzip "$zipfile" "$file"; then
    DEBUG "Can't unpack the zipfile"
    return 1
  fi

  if ! ls -l "$file" | grep -q "$filesize"; then
    DEBUG "unpacked filesize is wrong"
    return 1
  fi

  # global
  image_file="$file"
}

##############################################################################
# Helper functions to manage USB drives.

# Return a list of base device names ("sda sdb ...") for all USB drives
get_devlist() {
  local dev
  local t
  local r

  # Are we on a mac?
  if [ -n "$DISKUTIL" ]; then
    for dev in $(diskutil list | grep '^/dev'); do
      r=$(diskutil info $dev | grep 'Ejectable\: *Yes') || true
      t=$(diskutil info $dev | grep 'Protocol\: *USB') || true
      if [ "$r" != "" ]; then
        if [ "$t" != "" ]; then
          echo "$dev" | sed 's,/dev/,,'
        fi
      fi
    done
  else
    # No, linux, I hope
    for dev in $(cat /proc/partitions); do
      [ -r "/sys/block/$dev/device/type" ] &&
      t=$(cat "/sys/block/$dev/device/type") &&
      [ "$t" = "0" ] &&
      r=$(cat "/sys/block/$dev/removable") &&
      [ "$r" = "1" ] &&
      readlink -f "/sys/block/$dev" | grep -q -i usb &&
      echo "$dev" || true
    done
  fi
}

# Return descriptions for each provided base device name ("sda sdb ...")
get_devinfo() {
  local dev
  local v
  local m
  local s
  local ss

  # Are we on a mac?
  if [ -n "$DISKUTIL" ]; then
    for dev in $1; do
      m=$(diskutil info $dev | grep 'Device \/ Media Name\:' | \
          sed 's/^[^:]*: *//') || true
      s=$(diskutil info $dev | grep 'Total Size\:' | \
          sed 's/^[^:]*: *\([^(]*\).*/\1/') || true
      echo "/dev/$dev  $s $m"
    done
  else
    # No, linux, hopefully
    for dev in $1; do
      v=$(cat "/sys/block/$dev/device/vendor") &&
      m=$(cat "/sys/block/$dev/device/model") &&
      s=$(cat "/sys/block/$dev/size") && ss=$(( $s * 512 / 1000000 )) &&
      echo "/dev/$dev ${ss}MB $v $m"
    done
  fi
}

# Enumerate and descript the specified base device names ("sda sdb ...")
get_choices() {
  local dev
  local desc
  local count

  count=1
  echo "0 - <quit>"
  for dev in $1; do
    desc=$(get_devinfo "$dev")
    echo ""
    echo "$count - Use $desc"
    count=$(( count + 1 ))
  done
}

# Make the user pick a USB drive to write to. On success, it sets the global
# variable 'user_choice' to the selected device name ("sda", "sdb", etc.)
choose_drive() {
  local show
  local devlist
  local choices
  local num_drives
  local msg
  local num

  show=yes
  while true; do
    if [ -n "$show" ]; then
      devlist=$(get_devlist)
      choices=$(get_choices "$devlist")
      if [ -z "$devlist" ]; then
        num_drives="0"
        msg="I can't seem to find a valid USB drive."
      else
        num_drives=$(echo "$devlist" | wc -l)
        if [ "$num_drives" != "1" ]; then
          msg="I found $num_drives USB drives"
        else
          msg="I found $num_drives USB drive"
        fi
      fi
      echo "

$msg

$choices
"
      show=
    fi
    prompt "Tell me what to do (or just press Enter to scan again): "
    read num
    if [ -z "$num" ] || [ "$num" = "?" ]; then
      show=yes
    elif echo "$num" | grep -q '[^0-9]'; then
      echo "Sorry, I didn't understand that."
    else
      if [ "$num" -lt "0" ] || [ "$num" -gt "$num_drives" ]; then
        echo "That's not one of the choices."
      elif [ "$num" -eq 0 ]; then
        quit
      else
        break;
      fi
    fi
  done

  # global
  user_choice=$(echo $devlist | cut -d' ' -f$num)
}

# Unmount a partition
unmount_partition() {
  if [ -n "$DISKUTIL" ]; then
    diskutil unmountDisk "$1" || ufatal "Unable to unmount $1."
  else
    umount "$1" || ufatal "Unable to unmount $1."
  fi
}

##############################################################################
# Okay, do something...

# Make sure we have the tools we need
require_utils

# Need a place to work. We prefer a fixed location so we can try to resume any
# interrupted downloads.
if [ -n "$WORKDIR" ]; then
  if [ ! -d "$WORKDIR" ] && ! mkdir "$WORKDIR" ; then
    warn "Using temporary directory"
    WORKDIR=
  fi
fi
if [ -z "$WORKDIR" ]; then
  WORKDIR=$(mktemp -d)
  # Clean up temporary directory afterwards
  trap "cd; rm -rf ${WORKDIR}" EXIT
fi

cd "$WORKDIR"
warn "Working in $WORKDIR/"
rm -f "$debug"

# Download the config file to see what choices we have.
warn "Downloading config file from $CONFIGURL"
fetch_url "$CONFIGURL" "$tmpfile" || \
  gfatal "Unable to download the config file"

# Separate the version info from the images
grep '^recovery_tool' "$tmpfile" > "$version"
grep -v '^#' "$tmpfile" | grep -v '^recovery_tool' > "$config"
# Add one empty line to the config file to terminate the last stanza
echo >> "$config"

# Make sure that the config file version matches this script version.
tmp=$(grep '^recovery_tool_linux_version=' "$version") || \
  tmp=$(grep '^recovery_tool_version=' "$version") || \
  gfatal "The config file doesn't contain a version string."
filevers=${tmp#*=}
if [ "$filevers" != "$MYVERSION" ]; then
  tmp=$(grep '^recovery_tool_update=' "$version");
  msg=${tmp#*=}
  warn "This tool is version $MYVERSION." \
    "The config file is for version $filevers."
  fatal ${msg:-Please download a matching version of the tool and try again.}
fi

# Check the config file to be sure it's valid. As a side-effect, this sets the
# global variable 'num_images' with the number of image stanzas read, but
# that's independent of whether the config is valid.
good_config || gfatal "The config file isn't valid."

# Make the user pick an image to download, or exit.
choose_image

# Download the user's choice
fetch_image "$user_choice" || \
  gfatal "Unable to download a valid recovery image."

if [ -n "$DEVICE" ]; then
  user_choice="${DEVICE#/dev/}"
  dev_desc="${DEVICE}"
else
  # Make the user pick a USB drive, or exit.
  choose_drive

  # Be sure
  dev_desc=$(get_devinfo "$user_choice")
fi
echo "
Is this the device you want to put the recovery image on?

  $dev_desc
"
prompt "You must enter 'YES' (all uppercase) to continue: "
read tmp
if [ "$tmp" != "YES" ]; then
  quit
fi

# Be very sure
echo "

I'm really going to erase this device. This will permanently ERASE
whatever you may have on that drive. You won't be able to undo it.

  $dev_desc
"

prompt "If you're sure that's correct, enter 'DoIt' now (case is important): "
read tmp
if [ "$tmp" != "DoIt" ]; then
  quit
fi
echo "

Installing the recovery image

"

# Unmount anything on that device.
echo "unmounting..."
for tmp in $(mount | grep ^"/dev/${user_choice}" | cut -d' ' -f1); do
  unmount_partition "$tmp"
done

# Write it.
echo "copying... (this may take several minutes)"

# Many BSD variants provide both normal /dev/FOO and raw /dev/rFOO devices,
# with the raw path being much faster. If that device exists, we'll use it.
if [ -e /dev/r${user_choice} ]; then
  user_choice="r${user_choice}"
fi
dd bs=4194304 of=/dev/${user_choice} if="$image_file" conv=sync ||
  ufatal "Unable to write the image."
sync

echo "

Done. Remove the USB drive and insert it in your Chrome notebook.

"

prompt "Shall I remove the temporary files now? [y/n] "
read tmp
case $tmp in
  [Yy]*)
    cd
    \rm -rf ${WORKDIR}
    ;;
esac

exit 0

```

---

### Post by HappinessNow on 2010-12-19
> **HappinessNow said:**
> So I accidentally locked my self out of my CR-48, I now need to recover chrome OS using Ubuntu (can only recover using Linux or Mac at this point)

So I have the following notice:

[IMG]http://www.google.com/help/hc/images/chromeos_ponyRecovery.png[/IMG]

from the Google Chrome OS recovery page:



So I have elected to use Ubuntu to recover my Chrome OS, and I have an 8gb flash drive ready.

I downloaded the recovery tool and have it open in gedit but I have no idea what to do with it, the instructions are quite confusing. Si I decided it Would be less complicated to manually build an image at this point...

Also it says I need root privileges so I am currently logged in as root

preceding to Manually build an image following these instructions:



Ok so I 

1. downloaded the latest_mario_beta_channel
2. Extracted the .bin file from the .zip (renamed it chromeos-recovery.bin)
3. Inserted a USB Flash drive into my Ubuntu computer
4. saw the drive name: /dev/sdb1
5. ran the command in the terminal:
sudo dd if=chromeos-recovery-bin of=/dev/sdb1

I get the following output:

dd: opening `chromeos-recovery.bin': No such file or directory

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178850&d=1292765528[/IMG]

Ok so I think I figured it out, just a matter of typing in the directory properly so sudo could find it:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178853&d=1292766870[/IMG]

ok going to try for receovery

---

### Post by HappinessNow on 2010-12-19
well that didn't work it says it is not a chromeos system...and oddly enough now Ubuntu isn't recognizing my flash drive like it did before

Edit: reformatting the flashdrive to Linux ext4 format...

---

### Post by bwhite82 on 2010-12-19
That recovery tool you run this way from a terminal (make sure you're in the same directory as the file):

> sudo sh linux_recovery.sh

---

### Post by bwhite82 on 2010-12-19
Additionally, the "manual" method failed because it looks like you weren't in the same directory as the .bin file.

---

### Post by HappinessNow on 2010-12-19
> **Soldierboy said:**
> That recovery tool you run this way from a terminal (make sure you're in the same directory as the file):soldierboy Thanks for the reply, I will try the recovery tool next, I just reformatted the flash drive again to linux ext2

so here is what I put in:


```
sudo dd if=/home/nexusix/Downloads/linux_recovery.sh of=/dev/sdb
41+1 records in
41+1 records out
21254 bytes (21 kB) copied, 0.00638444 s, 3.3 MB/s
```

well that didn't work either

---

### Post by tgalati4 on 2010-12-19
How did you break it originally?

---

### Post by bwhite82 on 2010-12-19
> **HappinessNow said:**
> soldieboy Thanks for the reply, I will try the recovery tool next, I just reformatted the flash drive again to linux ext2

so here is what I put in:


```
sudo dd if=/home/nexusix/Downloads/linux_recovery.sh of=/dev/sdb
41+1 records in
41+1 records out
21254 bytes (21 kB) copied, 0.00638444 s, 3.3 MB/s
```

well that didn't work either


You're mixing up the two files: The .bin is for the manual method, thats the one you would "dd". The .sh (sh stands for shell script) is for the automated method. That method should work. Try this:

> chmod +x ~/Downloads/linux_recovery.sh

followed by:

> sudo sh ~/Downloads/linux_recovery.sh


---

### Post by bwhite82 on 2010-12-19
> **tgalati4 said:**
> How did you break it originally?

I am interested in this as well. Seems fairly bulletproof.

---

### Post by HappinessNow on 2010-12-19
> **Soldierboy said:**
> I am interested in this as well. Seems fairly bulletproof.
I finally got it working, needed to reformat flashdrive back to fat32, and not change the name of the .bin file

system recovery is almost complete...

I opted for the manual rebuild

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178859&d=1292774042[/IMG]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=178860&d=1292774042[/IMG]

I didn't break it I accidently locked myself out, this image is more accurate of what happened:

[http://goo.gl/qNfEp](http://goo.gl/qNfEp)

I had tweaked the user setting and some how locked myself out.

---

### Post by bwhite82 on 2010-12-19
Cool glad you got it working. Perhaps file a bug report about what happened?

---

### Post by HappinessNow on 2010-12-19
> **Soldierboy said:**
> Cool glad you got it working. Perhaps file a bug report about what happened?I have been in touch with the Team Lead of The Chrome Notebook Ninja Team, I emailed him directly with my experience and a link back to this thread. :p

---

### Post by benbrookshire on 2010-12-19
Cool, this will totally come in handy if I ever need to restore (or get bored and want to try it out to learn something). Cheers!

---

### Post by naveed.akter on 2010-12-21
Hey can someone guide me through this? I'm having the same exact problem, even got there the same way, tweaked user settings and locked myself out.

I have no clue what you did. (I'm a linux noob, I just happen to have Ubuntu live CD handy :)

---

### Post by tgalati4 on 2010-12-21
ChromeOS has "verified boot" which I assume is some sort of checksum on the boot image.  If that changes, then it forces you to restore.  Obviously changing some parameters "behind the scenes" causes the checksum to change and thus trips the lockout.  Changing user settings should not trip this, so it's either a bug or a feature.

---

### Post by Elfy on 2010-12-21
As with other Os support requests the best place for this would have been on whatever forum google have for support.

closing

---

