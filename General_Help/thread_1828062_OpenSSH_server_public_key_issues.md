---
title: "OpenSSH server public key issues"
date: 2011-08-18
forum: General Help
---

### Post by JoeDuncan on 2011-08-18
I am having a very strange issue with OpenSSH server.

I have a brand-new clean install of 64bit Ubuntu 11.04 Desktop.

The user I created during the install can access the machine via SSH using a public key just fine. Subsequently created users can only login once using their public key, but not after that.

I followed the exact same procedure with every user (including the one created during setup):

1) Generate an SSH-2 RSA keypair using Putty (I'm connecting to the Ubuntu machine from Windows)
2) Log in to the box via SSH with password.
3) mkdir .ssh; chmod 700 .ssh; cd .ssh; nano authorized_keys;
4) Cut and paste the "Public key for pasting into OpenSSH authorized_keys file:" text from Putty into nano.
5) Save "authorized_keys" and exit nano.
6) chmod 600 authorized_keys
7) Log out of box
8) Load key in Pageant
9) Reconnect to box using Putty

For the user I created during setup, this worked like a charm and I have had no further issues.

For any other user I have created manually, I do the above process and the very first time I try to login via SSH using the public key, it works fine. However, those users can't ever connect with the public key again after that.

I can reliably reproduce this phenomena (three times already!!!)

Here's some /var/log/auth.log output:

>>>>>>>>>>>>>>> Logging in using public key for user1

Aug 17 22:17:42 heimdall sshd[2662]: Connection from AAA.BBB.CCC.DDD port 52700
Aug 17 22:17:43 heimdall sshd[2662]: Found matching RSA key: 6a:7c:d5:3f:ba:a7:3e:18:cb:61:9f:3c:4a:06:45:13
Aug 17 22:17:43 heimdall sshd[2662]: Found matching RSA key: 6a:7c:d5:3f:ba:a7:3e:18:cb:61:9f:3c:4a:06:45:13
Aug 17 22:17:43 heimdall sshd[2662]: Accepted publickey for user1 from AAA.BBB.CCC.DDD port 52700 ssh2

>>>>>>>>>>>>>>> Logging out for user1

Aug 17 22:17:50 heimdall sshd[2747]: Connection closed by AAA.BBB.CCC.DDD
Aug 17 22:17:50 heimdall sshd[2747]: Transferred: sent 3296, received 2024 bytes
Aug 17 22:17:50 heimdall sshd[2747]: Closing connection to AAA.BBB.CCC.DDD port 52700
Aug 17 22:17:50 heimdall sshd[2662]: pam_unix(sshd:session): session closed for user user1

>>>>>>>>>>>>>>> Subsequent login attempt(s) for user1

Aug 17 22:18:03 heimdall sshd[2875]: Connection from AAA.BBB.CCC.DDD port 52702
Aug 17 22:18:04 heimdall sshd[2875]: Failed publickey for user1 from AAA.BBB.CCC.DDD port 52702 ssh2

When I tell putty to produce a log, the only relevant entry is:

"Server refused public key"

This is clearly a user/public key configuration issue, as my initial user has no problems and can connect fine. I created user1, user2, and user3 and setup the SSH connection exactly as I did for user0 (my initial user) - but they can only connect via public key on the first attempt, and not subsequently.

I can't see any real differences between user0 and the others (user0 is a sudo user, but I don't want the others to be and it's not a requirement for an SSH login).

The other users CAN login with SSH via password, but this is unacceptable, I need pubkey logins.

I have verified that the users' ".ssh" and "authorized_keys" have the correct permissions (only accessible by the user) and that those permissions do not change between the first pubkey login and the second. Users 1-3 have exactly the same permissions on these files as user0 does.

I also went through user0's group list and made sure user's 1-3 are in all the same groups except for admin and sudo.  I also added all users (0-3) to the "ssh" group, although user0 was able to login fine via pubkey without being part of this group.

Does anyone have any idea where I should look or what I should try next??? This is very frustrating.

Thanks in advance!

---

