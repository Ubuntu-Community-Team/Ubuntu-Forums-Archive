---
title: "Password security"
date: 2012-05-19
forum: General Help
---

### Post by Welly Wu on 2012-05-19
I installed Ubuntu 12.04 64 bit Long Term Support and I am wondering what kind of encryption cipher and hash algorithm is used to secure my Administrator password. What is being used? Can I change it? I would like to use Blowfish at 448 bits and I want to be sure that I can login and logout of my system. How do I change the default cipher and hash algorithm used to secure my Administrator password or any other users on my system? I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD.

---

### Post by Welly Wu on 2012-05-19
I just found out that Ubuntu 12.04 64 bit LTS uses SHA-512 hash algorithm. However, what cipher is used to encrypt my Administrator password? I also found out that I could use Blowfish at 448 bits, but how do I do this and ensure that I can login and logout of my system along with using the sudo command?

---

### Post by The Cog on 2012-05-19
It's my understanding that the passwords are not stored using a cipher, which is reversible and could allow recovery of the original password. Instead, passwords are stored using a hash which means that the original passwords are not recoverable. The system asks the user for the password as they log in, applies the hash algorithm and then compares the hash of the given password with the stored hash of the correct password.

Of course, if you know the stored hash, you can try to guess what the original password was by trying diferent possibilities and seeing which one gives the same hashed value, but you don't actually know you have the original password, just that you have found a word that produces the same hash. And I think the hasher adds extra stuff to the password before hashing it, just to make the guessing game harder.

---

### Post by Welly Wu on 2012-05-19
Your explanation sounds plausible since I am an expert on cryptography. A hash algorithm such as Secure Hash Algorithm 2 at 512 bits is a one way irreversible conversion of plain text into cipher text. A cryptographic cipher is reversible since it allows decryption. It also permits a wide array of cryptanalytic attacks both known and future attacks which will always get better. I posed my original post and question out of curiosity. I think that the default password security using SHA-512 is the most secure method of storing user passwords especially Administrator passwords.

---

### Post by Cheesemill on 2012-05-19
Password hashing settings are defined in /etc/pam.d/common-password
You can edit this file to change the hashing mechanism that is used, see 'man pam_unix' for more details.

Bear in mind that if you make any changes to this file it doesn't automatically re-hash your passwords with the new settings, you have to change your password to take advantage of on changes you've made.

---

### Post by Grandma_DOG on 2012-05-20
> **Cheesemill said:**
> Password hashing settings are defined in /etc/pam.d/common-password
You can edit this file to change the hashing mechanism that is used, see 'man pam_unix' for more details.

Bear in mind that if you make any changes to this file it doesn't automatically re-hash your passwords with the new settings, you have to change your password to take advantage of on changes you've made.

Is there a possible backward compatibility issue on this?

---

### Post by Welly Wu on 2012-05-20
I studied and researched this subject matter quite extensively and I do not plan to make any changes. I am not going to edit the PAM module for common-password. SHA-512 is well understood by cryptographers, cryptanalyst, and mathematicians. It is highly resilient and highly robust. It is widely agreed upon to be nearly impossible to reverse or crack.

I used [http://www.passfault.com](http://www.passfault.com) to analyze my LUKS/LVM pre-boot authentication password and my Ubuntu Administrator password. I strengthened them using passfault exponentially and I saved my credentials in KeePass2 and LastPass Premium using my Yubico Yubi Key pair.

In fact, choosing Blowfish at 448 bits is considerably weaker and a brute force attack has the potential to crack my Ubuntu Administrator password if I used it to replace SHA-512. Blowfish is an unbroken cipher that permits decryption of cipher text back to its original plain text using the right key. This is a security risk if it is applied to my Ubuntu Administrator password.

---

### Post by Welly Wu on 2012-05-20
By the way, SHA-512 is not vulnerable to collision attacks because it implements a unique salt and Canonical uses the industry standard pseudo random number generator which has the end result of generating a unique, complex, random, highly resilient and highly robust one way hash. If you have the new Intel Third Generation Ivy Bridge Core i5 or Core i7 CPU, then it has the new Bull Mountain random number generator which makes the salting and random number generator much much more random and complex which results in a much much more safer and more secure encrypted cipher text using the industry standard Advanced Encryption Standard cipher at 128, 192, and 256 bits key space. Intel Ivy Bridge Core i5 and Core i7 CPUs support AES-NI or New Instructions to further enhance the speed and performance of AES functions especially when used in combination with current generation Intel SATA-III 6 GB/s Solid State Drives such as the Intel 520 Cherryville SSD. If you meet all of these high end requirements, then you have cutting edge cryptographic capabilities.

---

### Post by Welly Wu on 2012-05-20
Canonical and Ubuntu will support Intel Third Generation Ivy Bridge CPUs in due time. Ubuntu supports AES-NI and it supports Intel 520 Cherryville SATA-III 6 GB/s SSDs.

---

