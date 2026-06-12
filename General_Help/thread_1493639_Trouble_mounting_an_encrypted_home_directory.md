---
title: "Trouble mounting an encrypted home directory"
date: 2010-05-26
forum: General Help
---

### Post by Arkeph on 2010-05-26
I attempted to preserve an encrypted home directory partition through an upgrade to 10.04, and all seemed to go well until I tried to access the directory, located in /media/bunchofnumbersandletters/username. The "Access Your Private Data" script doesn't seem to do anything at all, so I used [these]("https://help.ubuntu.com/community/EncryptedPrivateDirectory") instructions. That, however, only let me see all of my still-encrypted files.

All repeated attempts ended up with me only being able to see the useless script and the readme telling me to use it. Any ideas on how to mount this encrypted directory?

---

### Post by Arkeph on 2010-06-01
In case this helps, this is a snippet of the syslog after a "successful" mount. The fnek sig referred to is *not* any of the three numbers recovered with the "ecryptfs-unwrap-passphrase" and "ecryptfs-add-passphrase --fnek" commands.

```
Jun  1 02:00:19 *User* kernel: [  358.569062]
 ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
Jun  1 02:00:19 *User* kernel: [  358.569067] Could not find key with description: [****************]
Jun  1 02:00:19 *User* kernel: [  358.569069] process_request_key_err: No key
Jun  1 02:00:19 *User* kernel: [  358.569072] ecryptfs_parse_tag_70_packet: Error attempting to find auth tok for fnek sig [****************]; rc = [-2]
Jun  1 02:00:19 *User* kernel: [  358.569075] ecryptfs_decode_and_decrypt_filename: Could not parse tag 70 packet from filename; copying through filename as-is
```

My guess is that I inadvertently double-encrypted the home partition, which means that, since I lack the old key, I can't even recover the old key with my old password. It's one of those locked-the-keys-inside-the-car sort of situations. The new key which I got after the second encryption would in this case be useless. 

I'm looking for a second opinion, so any input would be appreciated.

---

### Post by Arkeph on 2010-06-06
bump

---

### Post by Arkeph on 2010-06-16
I ended up simply reformatting and using my back-ups.

---

