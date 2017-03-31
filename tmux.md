tmux cheatsheet
===============

Shunliu Zhao
Last updated: 2017-jan-19


## configure tmux ##

vim ~/.tmux.conf

	##reload config
	## ctrl+a and then :
	## type in 'source-file ~/.tmux.conf'
	##OR
	## tmux source-file ~/.tmux.conf
	
	set-option -g prefix C-z
	unbind-key C-b
	bind-key C-a send-prefix
	
	# split panes using | and -
	bind \ split-window -h -c '#{pane_current_path}'
	bind - split-window -v -c '#{pane_current_path}'
	unbind '"'
	unbind %
	
	# do not allow renaming
	set-option -g allow-rename off
	
	# resize window
	setw -g aggressive-resize on
	
	# switch panes using Alt-arrow without prefix
	## conflict with terminator config
	#bind -n M-Left select-pane -L
	#bind -n M-Right select-pane -R
	#bind -n M-Up select-pane -U
	#bind -n M-Down select-pane -D
	
	##ref: http://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/
	##ref: https://mutelight.org/practical-tmux


## use tmux ##

* start a session named "alt": tmux new -s alt
 * re-attach a session(acting independently): tmux new -t alt
* detach a session: C-a d
 * detach from the old instance and attach: tmux attach -d -t alt
* attach (multiple instances allowed): tmux attach -t alt
* list sessions: tmux ls
* rename: 'tmux rename -t alt alpha-alt';
  or, 'C-a $'
* Switch between sessions:
 * C-a (          previous session
 * C-a )          next session
 * C-a L          ‘last’ (previously used) session
 * C-a s          choose a session from a list
* kill a session "alpha-alt":  tmux kill-session -t al

* create a new window: C-a c
* rename a window: C-a ,
* Switch between windows:
 * C-a 1 ...      switch to window 1, ..., 9, 0
 * C-a n/p        next/previous window
 * C-a l          ‘last’ (previously used) window
 * C-a w          choose window from a list

* split into two vertical panes: C-a "
 * with new config: C-a \
* split into two horizontal panes: C-a %
 * with new config: C-a -
* resize by holding 'C-a' and pressing up/down arrow
* Switching between panes:
 * C-a left       go to the next pane on the left
 * C-a right      (or one of these other directions)
 * C-a up
 * C-a down
 * C-a o          go to the next pane (cycle through all of them)
 * C-a ;          go to the ‘last’ (previously used) pane
* Switch the positions of two panes
 * C-a {        move the current pane to the previous position
 * C-a }        move to the next position
 * C-a C-o      rotate window ‘up’
 * C-a !        move the current pane into a new separate window
* kill a pane: C-a x

* copy by using a mouse 
 * press 'ctrl + space' and hold, and then use mouse to select a rectangular field
 * or, press 'ctrl + alt' and hold, and then use mouse

* ref
 * http://robots.thoughtbot.com/a-tmux-crash-course
 * https://gist.github.com/andreyvit/2921703
 * http://cheat.errtheblog.com/s/tmux
