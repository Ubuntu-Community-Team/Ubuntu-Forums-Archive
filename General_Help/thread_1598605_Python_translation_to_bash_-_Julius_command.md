---
title: "Python translation to bash - Julius command"
date: 2010-10-16
forum: General Help
---

### Post by dark-triad on 2010-10-16
Hi, 
can anyone help me with a generic script template for julius to execute upon speech recognition, im using the example command.py which comes with julius and it works fine but i would like to customize it for further use but would like to use bash as i cant code in python i have been learning bash, so if anyone can give me just a brief example or simple translation in bash i would appreciate it, im not sure how to get the recognized output from julius into a bash variable, I know there are a few code gurus here. It doesnt need to be rhythmbox/banshee specific like the python script, just something simple that works in a simliar way that i can get started on to execute different commands, im after something like:

```
recognized word from julius

commands:
word=command
word=command
word=command
word=command
etc

if recognised word = any of the words above
then
execute recognized command
else
echo no match found
```

this is the python example from julius:
```
#! /usr/bin/python -u
# Command and Control Application for Julius
#
# How to use it:
#  julius -quiet -input mic -C julian.jconf 2>/dev/null | ./command.py

import sys
import os

class Rhythmbox:
	
	name = "Rhythmbox"
	
	commands = {
			'play': 'play',
			'pause': 'pause',
			'next': 'next',
			'prev': 'previous',
			'show': 'notify',
			'pause': 'pause',
			'silence': 'pause',
	}
	
	def parse(self, word):
		if word in self.commands:
			return 'rhythmbox-client --%s' % self.commands[word]

class Banshee:
	
	name = "Banshee"
	
	commands = {
			'play': 'play',
			'pause': 'pause',
			'stop': 'stop',
			'next': 'next',
			'prev': 'previous',
			'pause': 'pause',
			'silence': 'pause',
	}
	
	def parse(self, word):
		if word in self.commands:
			return 'banshee --no-present --%s %% ' % self.commands[word]

class CommandAndControl:
	
	def __init__(self, file_object):
		
		# Determine which media player to use
		if os.system('ps xa | grep -v grep | grep rhythmbox >/dev/null') == 0:
			self.mediaplayer = Rhythmbox()
		elif os.system('ps xa | grep -v grep | grep banshee >/dev/null') == 0:
			self.mediaplayer = Banshee()
		elif os.system('which banshee >/dev/null') == 0:
			self.mediaplayer = Banshee()
			os.system('bash -c "nohup banshee >/dev/null 2>&1 <&1 & disown %%"')
		elif os.system('which rhythmbox >/dev/null') == 0:
			self.mediaplayer = Rhythmbox()
		else:
			print 'Couldn\'t find a supported media player. ' \
				'Please install Rhythmbox or Banshee.'
			sys.exit(1)
		print 'Taking control of %s media player.' % self.mediaplayer.name
		
		startstring = 'sentence1: <s> '
		endstring = ' </s>'
		
		while 1:
			line = file_object.readline()
			if not line:
				break
			if 'missing phones' in line.lower():
				print 'Error: Missing phonemes for the used grammar file.'
				sys.exit(1)
			if line.startswith(startstring) and line.strip().endswith(endstring):
				self.parse(line.strip('\n')[len(startstring):-len(endstring)])
	
	def parse(self, line):
		# Parse the input
		params = [param.lower() for param in line.split() if param]
		if not '-q' in sys.argv and not '--quiet' in sys.argv:
			print 'Recognized input:', ' '.join(params).capitalize()
		
		# Execute the command, if recognized/supported
		command = self.mediaplayer.parse(params[1])
		if command:
			os.system(command)
		elif not '-q' in sys.argv and not '--quiet' in sys.argv:
			print 'Command not supported by %s.' % self.mediaplayer.name

if __name__ == '__main__':
	try:
		CommandAndControl(sys.stdin)
	except KeyboardInterrupt:
		sys.exit(1)
```

Can this be done in bash?
Any help appreciated - Thanks!

---

