---
title: "How can I make a script non-interactive"
date: 2009-10-29
forum: General Help
---

### Post by lotuseclat79 on 2009-10-29
I want to add the following command to a script I execute as root to be able to delete some language-packs from the Live CD environment, however, it asks the question - Do you want to continue [Y/n]? which requires an answer.

# apt-get remove --purge `dpkg-query -W --showformat='${Package}\n' | grep language-pack | egrep -v '\-en'`

How can I make the script execute the command non-interactively by somehow feeding the answer to the command as it is executed instead of having to watch the script and answer it when the question comes up for an answer?

The apt-get command is the ELF 32-bit executable asking the question [Y/n], i.e. it is not a script.

Tia,

-- Tom

P.S.  Ok, this was easier than I thought - for a minute I thought I was going to have to use the expect command which would have complicated the issue which was simply to replace the one line command with the following two lines:
echo "Y" > ans
apt-get remove --purge `dpkg-query -W --showformat='${Package}\n' | grep language-pack | egrep -v '\-en'` <ans

The above change creates a small answer file named ans with the answer, Y.  The anser file is then fed as input into the apt-get command by appending <ans or < ans to the end of the command on the same line.  It is that simple, sort of like adding the following to the script inline, but on the same line as the command:
<command> <<EOF
Y
EOF

---

