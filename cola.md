git commit --amend

git checkout -- quarto.txt

git reset HEAD~4 --hard

git reset HEAD~4 --soft

git reset HEAD~1 --hard

git reset HEAD~4

git clean -df

git rebase HEAD~4 -i

#4 r 
#3 s
#2 e
#1 d

pick
reword
edit
squash
fixup
exec
drop

The first two columns are key: the first is the selected command for the commit identified by the SHA in the second column. By default, rebase -i assumes each commit is being applied, via the pick command.

To drop a commit, just delete that line in your editor. If you no longer want the bad commits in your project, you can delete lines 1 and 3-4 above.

If you want to preserve the contents of the commit but edit the commit message, you use the reword command. Just replace the word pick in the first column with the word reword (or just r). It can be tempting to rewrite the commit message right now, but that won't work—rebase -i ignores everything after the SHA column. The text after that is really just to help us remember what 0835fe2 is all about. When you've finished with rebase -i, you'll be prompted for any new commit messages you need to write.

If you want to combine two commits together, you can use the squash or fixup commands, like this:

rebase-interactive2

squash and fixup combine "up"—the commit with the "combine" command will be merged into the commit immediately before it. In this scenario, 0835fe2 and 6943e85 will be combined into one commit, then 38f5e4e and af67f82 will be combined together into another.

When you select squash, Git will prompt us to give the new, combined commit a new commit message; fixup will give the new commit the message from the first commit in the list. Here, you know that af67f82 is an "ooops" commit, so you'll just use the commit message from 38f5e4e as is, but you'll write a new message for the new commit you get from combining 0835fe2 and 6943e85.

When you save and exit your editor, Git will apply your commits in order from top to bottom. You can alter the order commits apply by changing the order of commits before saving. If you'd wanted, you could have combined af67f82 with 0835fe2 by arranging things like this:



