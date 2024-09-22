# btrm
 `btrm` is a helper script to quickly find and remove specific files for directories across all snapshots on btrfs.
 
No longer do you have to delete full snapshots just to free up space, just delete that specific file across all subvolumes.

Usage
```
Usage: ./btrm -s <snapshot-dir> -f <file-to-remove>
  -s <snapshot-dir>    Path to Snapper snapshots directory
  -f <file-to-remove>  Relative path from snapshot-dir to the file
  -h                   Show this message
```
`snapshot-dir` should be the path to the root of your snapshots (e.g. `/.snapshots`, `/home/.snapshots`)
`file-to-remove` is a path relative from `snapshot-dir` for the file to remove.

Let's say I have snapshots that that contain a file `/home/jason/foo/bar`. If I wanted to remove `bar` from every snapshot, the command would be as follows:
`btrm -s /home/.snapshots -f foo/bar`

This will remove `bar`, but keep `foo`.

It takes into account if your snapshot is read-only and sets it back if it was.

**I have not done extensive testing. Ut may not work correctly, but so far has worked for my use cases.**
