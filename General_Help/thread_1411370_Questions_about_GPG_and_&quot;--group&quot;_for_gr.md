---
title: "Questions about GPG and &quot;--group&quot; for group encryptions."
date: 2010-02-19
forum: General Help
---

### Post by Th3Professor on 2010-02-19
I'm looking for a way to include a group of people in gpg file encryption/decryption (not email-based, just gpg encrypted files) without having to incorporate individual names, yet also such that more people can be added to the group in the future and that they will be able to access previously encrypted files because they joined the group after the old files were encrypted.

Does the "--group" option in gpg serve this purpose?

Or is there another way to go about it?

I checked the man file for gpg, read the bit on --group and similar group-related information and it has this:

>  --group name=value1
              Sets up a named group, which is similar to aliases in email pro&#8208;
              grams.  Any time the group name is a recipient (-r or  --recipi&#8208;
              ent),  it  will  be  expanded  to the values specified. Multiple
              groups with the same name are automatically merged into a single
              group.

              The  values are key IDs or fingerprints, but any key description
              is accepted. Note that a value with spaces in it will be treated
              as  two  different  values. Note also there is only one level of
              expansion --- you cannot make an group that  points  to  another
              group.  When  used from the command line, it may be necessary to
              quote the argument to this option  to  prevent  the  shell  from
              treating it as multiple arguments.

       --ungroup name
              Remove a given entry from the --group list.

       --no-groups
 Remove all entries from the --group list.I found on a google search the following information someone provided regarding adding a line to the gpg.conf file:

**group name_you_want_to_use = keyid1 keyid2 keyid3 keyid4**

That is a little confusing.

Does that mean that people with their own individual keys can be added or removed from the group?

Does the group have its own key?

If an individual's key is in the group then can they decrypt files that have been encrypted before they joined the group using the "group key" as recipient?

But if their key has been removed from the group then can they still decrypt previous files that were encrypted using the "group key" as recipient?

If I add people to a group via gpg.conf (using the line in bold type font above), and if I later want to add only one person to the group, can I add them with the gpg command with option "--group name=value1" or must I re-enter all of the previous keys in addition to the new one?

If I want to remove only one person from the group, can I do that with either the gpg command and "--ungroup name" or alternately remove their key/name from the line in the gpg.conf file?

Do I have to add their public key to my keyring before I can add their key to the group?

If a "group key" (a singular "group recipient") can be created through either "--group" or the group line in the gpg.conf, and if I create a group, then will only I have administrative control over who is added/removed from the group, or will anybody in the group be able to add/remove anybody from the group?

Thank you for your help!

EDIT:

...nevermind.

---

### Post by yuler on 2011-11-29
A "group key" is simply an alias for multiple public keys on your keyring.  It is similar to group name in email programs.  It should not have been called group key, but group name.  You must have the public keys of the recipients to add to the group. 

For example:

I have public keys for UserA and UserB
I create a group called "MyGroup"
I add UserA and UserB to MyGroup
I encrypt to MyGroup, which will encrypt to UserA and UserB public keys

---

