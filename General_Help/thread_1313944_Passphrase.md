---
title: "Passphrase"
date: 2009-11-04
forum: General Help
---

### Post by Orian90 on 2009-11-04
I upgraded to ubuntu 9.10 today, and encrypted my home partition. However, on login, I got a screen saying something about "passphrase". By accident, I clicked it away, and now I don't know what it does/is. I googled a bit, and found out it has something to do with the encryption, but I was wondering, what exactly is it, and do (and how) have to restart it?

Thanks in advance.

---

### Post by jdunn on 2009-11-04
By default, your user login decrypts HOME.  In the event something goes horribly wrong, (ex: you lose your login pw) you are given a passphrase after installation that will also decrypt HOME.  The passphrase is an ungodly number of alphanumeric digits.  There is probably some way to find out the passphrase again but I don't know how, as this feature is new to me and I just installed 9.10 yesterday.

---

### Post by undecim on 2009-11-04
It was a message telling you that you need to get a copy of your encryption key put somewhere safe. If you ever need to recover your data manually (i.e. your computer breaks, and you need to use a livecd to get your files back), you will need this key.```
ecryptfs-unwrap-passphrase /home/.ecryptfs/username/.ecryptfs/wrapped-passphrase
```
That command will ask you for a passphrase. Type in the passphrase you use to log in, and it will return with a string of hexadecimal digits. Write these down and put them somewhere safe. This is the key to your home directory, so don't leave it anywhere that a malicious person (i.e. a burgler) could have access to it.

A quick explanation: ecryptfs uses your login passphrase to unlock your home directory. But since you don't want to wait for your entire home directory to be re-encrypted every time you change your passphrase, ecryptfs makes a random key to encrypt your home directory and encrypts that key using your passphrase. when you log in, your passphrase is used to decrypt the key for your home directory.

---

### Post by Orian90 on 2009-11-05
Thank you for your help. However, when I enter my password, I get an error message:
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs

Any idea what this means/how I can fix it?

---

### Post by undecim on 2009-11-05
> **Orian90 said:**
> Thank you for your help. However, when I enter my password, I get an error message:
Error: Unwrapping passphrase failed [-5]
Info: Check the system log for more information from libecryptfs

Any idea what this means/how I can fix it?

Make sure that the file you are trying to unwrap exists, and that you typed your login correctly (check caps lock).

Also, as directed by the error, check your syslog for anything abour ecryptfs: ```
grep ecryptfs /var/log/syslog
```

---

### Post by Orian90 on 2009-11-05
Thank you. I tried it again, and still the same error. I'm 100% sure I did type it right now.

I have no idea how to find out the file exists, maybe you can tell me how?

And about the log, this is what it says:
```
Nov  4 09:13:06 Laptop-van-Imre kernel: [ 1141.733555] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfper5oGxMwxgO2JXchGAeZYnpqB1H.LZJ5s3YISoFZA0fKC-vYpR-x2sd0hNUDqEt8A6hburx19gQE-SiZfQ48SuMPTRs381xZcYX-abgFlI7wagJFACG-vCbttRHHd43vvDlgajIf0SjSEhdGdCaweXUKMXkxrTBOeb8I.BGCccpW.nZ2oMAvKKtbLR2KQ-godh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:20 Laptop-van-Imre kernel: [ 1156.409052] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpFDFLXhGwUkJwA9BsKmvkw9qlaSiCVb9KmZkqEAA4RUQLBDYSVxvbwHV6Guyu4CBL3Omv1sF3gdrmOrOqQV2Rf1-ybatFi3.Kai6ej.VhvF2H6H5A-39NxA7hCfsZegpkVI123bSgCeF3W-EL.XBpX6h10AXW3eEEdb6tCVxkC31hAvj2UyiSagYNocNlhuavdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:25 Laptop-van-Imre kernel: [ 1161.550183] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpU8HF5FNrE1diSDPUgvw9eFf4MGPozniUvCK2DYx2qtxseY-i8To99pH5L5.lhbACYbjOcJTxxARXOsm7Jzxcv34z5TlTcNKcXnuI0Z9nRRnaHcVUV2ESFEL0FfuSvGuLG0Hf28n7iT2lnrUMRVb6Vd.72XCxmO6j9wqHYyBYRVvermmMj8SDEB73lyG9nbuhdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:27 Laptop-van-Imre kernel: [ 1163.407570] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfper5oGxMwxgO2JXchGAeZYnpqB1H.LZJ5s3YISoFZA0fKC-vYpR-x2sd0hNUDqEt8A6hburx19gQE-SiZfQ48SuMPTRs381xZcYX-abgFlI7wagJFACG-vCbttRHHd43vv5qtFdSYmQYT3g-..U-3SO.yLtKvApN6CA77RVrfZISreByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:34 Laptop-van-Imre kernel: [ 1170.001305] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfper5oGxMwxgO2JXchGAeZYnpqB1H.LZJ5s3YISoFZA0fKC-vYpR-x2sd0hNUDqEt8A6hburx19gQE-SiZfQ48SuMPTRs381xZcYX-abgFlI7wagJFACG-vCbttRHHd43vrYxMv6NBbtzTpeZ2VwW8ZyqQHBYEWV6moTHmnkUFX6WreByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:34 Laptop-van-Imre kernel: [ 1170.233548] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpfkcWvLn0140cZcdBcx1sagJ4-I.9vLMWo7WbI12XNmBCNsHePEABe.vWULFm7EJabTtoB1IcxsvgeO8AP-N4jO8SpRPjcFfCGwMT8J55UZIPvwqtaBJxUaz95aAZ6oDSpVpVQDMsmUxs41jzReNDd98Gz5ToR5ajd-WevV1RZPbqZBP5SYRmMgUpDXc3qR6rdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:38 Laptop-van-Imre kernel: [ 1173.743208] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpRJiiKi9.JTBDoS4fxhYS.f40vkMl8HdY.KWzxcjhY5LK-ubdj7nM3S4KUbT-z9Qd6pBk.UikeJissSDibKlX-dutQZrauXOqLsgP3aLOBjuELAzaUNt1mpsGZkmgLwZ4pkxry-ZwxuQFfbg36lwKE9LnBtAtH6tFlw78bUPkRmyreByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:38 Laptop-van-Imre kernel: [ 1173.922907] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpc13zd4.KXuw.bhQc-hLNNv5bY7NgQ.mfwLSw2gDNovGwbgcf3kC7AXVEP44X3jVxSgSBPOmVVC5uNpU1SfudyqV3.Kl5oyxOTjh2qltNESPsn7ogxJ0rg1RKZ3mf9aZzFm4dJPv7lR6ksrsePkPDc9LnBtAtH6tFlw78bUPkRmyreByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:39 Laptop-van-Imre kernel: [ 1174.989509] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpwIJvqLRGxr77.VzTkTPiL3HWLtkdSdiK04KLphOC2VJabTuCduZpoc.tKxLIopIvLBqE7jG0hmJZWkPSsqeXlaOhlgq0QhoMbZ.IXPEusoT3YuJrrb5QRnFdA.mcFWuc5MVG4Lt.4oNnXXtrOj-o4ax9Tj1idUBAL86oZz6GGSereByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:39 Laptop-van-Imre kernel: [ 1175.447573] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpRJiiKi9.JTBDoS4fxhYS.f40vkMl8HdY.KWzxcjhY5LK-ubdj7nM3S4KUbT-z9Qd6pBk.UikeJissSDibKlX-dutQZrauXOqLsgP3aLOBjuELAzaUNt1mpsGZkmgLwZ4220toTZxdzjVM.wAzQSWzjpT6mgJHwXZ-K6sM8.F5PqDFVttvzWAy-XE.L-cRYXfdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:40 Laptop-van-Imre kernel: [ 1176.573705] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpU8HF5FNrE1diSDPUgvw9eFf4MGPozniUvCK2DYx2qtxseY-i8To99pH5L5.lhbACYbjOcJTxxARXOsm7Jzxcv34z5TlTcNKcXnuI0Z9nRRnaHcVUV2ESFEL0FfuSvGuLodyIypom2vOFpuwwNhj8IGIYfcywBSEyB4NPiOoBnoGreByu4zSaezC17vQvoUGLdh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:13:54 Laptop-van-Imre kernel: [ 1189.898172] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Ffbucxeh5sF6DET0Dc8QP.XJGLRQchmtAFfpLH0OYK6si2Dad0CTwHkosAq835sRnbuGGdBok6mYeCWjrfYWgn6itXa-5hcrhqPAQsHTKlrGOF8zz-1OMCA5KOS3sWU6eTI4d-3H4UMj.U4nEwfvdW7UXMY.Cbw.WZ3pf7sT50usZR0AO3Do2h0o1ZsR9XYMC6-k6wMhMzLsqQ4YOHfxfGZ2JnbyBVW-4E52dh7raGk4nU3Jmtp1hSosvk--]
Nov  4 09:14:03 Laptop-van-Imre kernel: [ 1199.330068] ecryptfs_lookup: lookup_one_len() returned [-36] on lower_dentry = [ECRYPTFS_FNEK_ENCRYPTED.Fg-7yeDOfFy2G1o5kXu0b4kMpIZrL89QiH2OxP4elYVCcVn9ZKXc8v3WunLxfzSaCm2coLPtbbM7FdriFFq8Hv.rtvSwMd27.fY6x1NkwgWV-QOqdTBG-rktycmSqHbWLyRODNccQ0Rr1XbaWfeB8eEPSWnspXDowofh71yq34N3ncul2XYnql2xKTfaQ9i3O0kIruhYmxEA2RR3m1qi2vagGMROiTv0mlN0i9ScrvcPxuOfwsAbhnjG.7SaobSN9-PC-JL9bICpvHXj]
Nov  5 12:01:51 Laptop-van-Imre ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/username/.ecryptfs/wrapped-passphrase] for reading
Nov  5 12:01:59 Laptop-van-Imre ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/username/.ecryptfs/wrapped-passphrase] for reading
Nov  5 23:18:43 Laptop-van-Imre ecryptfs-unwrap-passphrase: Error attempting to open [/home/.ecryptfs/username/.ecryptfs/wrapped-passphrase] for reading 
```

I have no idea what it means, anyone does?

---

### Post by fluffman86 on 2009-11-05
You don't have to give the file name.  Just do
```
ecryptfs-unwrap-passphrase
```

Then enter your login password.

---

### Post by Orian90 on 2009-11-06
> **fluffman86 said:**
> You don't have to give the file name.  Just do
```
ecryptfs-unwrap-passphrase
```

Then enter your login password.

Thank you, that was the way to it work :)

---

