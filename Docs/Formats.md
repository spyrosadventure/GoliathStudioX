# Goliath File Formats
## PKZ
A **PKZ** file is a compressed **PAK** file, it quite literally just means **Pak-Zlib**.

**PKZ** files could be uncompressed **PAK files**, but most of the time they are compressed.

## PAK
A **PAK** file is a container of chunks/objects. It contains a very large hierarchy of these chunks, and each chunk header is formatted like this:
Only chunks that do not have the "Has Sub-Chunks?" option enabled, can contain data.

[GS9 / GS8 / GS7]

| Chunk ID + 0x80000000 | Chunk Options           | 64-bit Length Value |
|-----------------------|-------------------------|---------------------|
| 0x04                  | 0x04 (0x02 each)        | 0x08                |

[GS6 and below]

| Chunk ID | Chunk Options | 32-bit Length Value |
|----------|-------------|---------------------|
| 0x04     | 0x04        | 0x04                |


### Chunk Options

| Option 1 | Option 2        |
|----------|-----------------|
| Version  | Has Sub-Chunks? |

## RESDB (Resource Database)
Used in Goliath prototype/early builds for resource debugging purposes.

**RESDB** files are usually just renamed **PAK** files with unique chunks.

Although they are renamed **PAK** files, they are little endian, even on big endian platforms.
