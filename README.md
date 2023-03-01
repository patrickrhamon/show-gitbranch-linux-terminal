# How change linux terminal to show git branch checkouted

1º - Run command in terminal: vim ~/.bashrc [Enter]
2º - Search for sentence: "if [ "$color_prompt" = yes ]; then" and add before "if" this function:

parse_git_branch() {
 git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/(\1)/'
}

3º - After add function, replace all validate sentence for this sentence:

if [ "$color_prompt" = yes ]; then
 PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[01;31m\]$(parse_git_branch)\[\033[00m\]\$ '
else
 PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w$(parse_git_branch)\$ '
fi


P.s.: You need change "if" and "else" values for P1.
