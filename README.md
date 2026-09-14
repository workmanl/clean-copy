# Clean Copy

[Use Clean Copy on The Cascade Hub](https://thecascadehub.com/tools/clean-copy/).

A standalone browser utility for inspecting and selectively removing supported image metadata blocks. Open `index.html` in a modern browser, or serve this directory with any static web server. No install, build, account or external dependency is needed.

## Usage

1. Drop images onto the page or choose them with the file picker.
2. Review the listed metadata and its decoded fields or text where available.
3. Checked blocks will be removed when you click **Download selected removed**. Color profiles and certain JPEG headers are kept by default.
4. Keep the original. The downloaded filename adds `-clean`.

**Select all** includes color and structural metadata. Removing these can change colors or orientation. **Select none** retains recognized blocks. Files with no supported removable blocks do not show a selective download button.

## Formats and processing

- JPG/JPEG: selective removal of supported pre-image APP and comment segments, including EXIF, XMP, ICC, Photoshop/IPTC and APP11 blocks that may contain C2PA/JUMBF.
- PNG: selective removal of text, EXIF, C2PA, timestamp and supported color chunks.
- WebP: selective removal of EXIF and XMP, with RIFF size and relevant VP8X flags updated. Other chunks are retained.
- Re-encode copy: uses the browser canvas decoder and encoder. Inputs whose MIME type is `image/png` export as PNG; other browser-decodable images export as JPEG at quality 0.92. Unsupported browser formats cannot be re-encoded.

The standalone file has no network requests, analytics, external scripts, storage or image uploads. It reads selected files in browser memory and downloads browser-generated copies. A hosting page or wrapper can have its own network behavior.

## Limits

This is a supported-block inspector, not a comprehensive metadata or authenticity audit. EXIF display covers selected fields and is capped at 40 rows; compressed PNG text is not decompressed. Signatures are not verified, APP11 is not proof of C2PA, and provenance keyword flags do not prove AI authorship.

Unknown PNG/WebP chunks and JPEG content after the first scan marker can remain. Malformed files may be only partly parsed. Selective removal preserves compressed image data, but removing orientation, color profiles or structural tags can change rendering. Re-encoding can change color and quality, discard animation, and lose transparency when exporting JPEG. Browser encoders may add basic format metadata. Neither route removes visible or invisible pixel watermarks or guarantees a particular platform label outcome.

Keep an original with provenance and attribution intact. Metadata removal does not replace any disclosure requirements that apply to your use.

Files are processed in memory, with no size limit or batch cancellation. Very large images or many files may exhaust browser memory. If decoding or saving fails, use another valid image or a smaller batch.
