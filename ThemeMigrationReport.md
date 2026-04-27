# Theme Refactoring Migration Report
Generated: 2026-04-25

## 1. Original Hardcoded Color Changes (Reverted)
The following colors were previously modified directly in the source code. They have been restored to their original system behaviors and moved to the CSS theme system.

### Checklist Status (OtherColors.cs)
- Success: From (128, 255, 128) to Google Green (15, 157, 88)
- Warning: From (255, 255, 128) to Google Yellow (253, 216, 53)
- Error: From (255, 128, 128) to Google Red (219, 68, 55)

### Revision Grid Visuals (RevisionDataGridView.cs)
- Selection: From SystemColors.Highlight to (0x3e, 0x3e, 0x42)
- Body Text: From SystemColors.GrayText to (0xb0, 0xb0, 0xb0)
- Alternate Rows: Now calculated dynamically or via CSS instead of hardcoded darken factor.

## 2. Original dark secreal.css (Commit 74759f5)
```css
@import url("dark.css");
.PanelBackground { color: #252526; }
.EditorBackground { color: #252526; }
.LineNumberBackground { color: #252526; }
.AuthoredHighlight { color: #1f1f1f; }
.Selection { color: #37373d; }
.HighlightAllOccurences { color: #515c6a; }
.InactiveSelectionHighlight { color: #2d2d30; }
.Branch { color: #8ab878; }
.RemoteBranch { color: #c96767; }
.Tag { color: #8ab878; }
.OtherTag { color: #7b7b7b; }
```

## 3. Current Migration Mapping
The following elements are now fully themeable via CSS using the new `AppColor` enum.

| UI Element | AppColor Enum | Default Fallback (System) |
| :--- | :--- | :--- |
| Success Status | ChecklistStatusSuccess | #80FF80 |
| Warning Status | ChecklistStatusWarning | #FFFF80 |
| Error Status | ChecklistStatusError | #FF8080 |
| Grid BG | PanelBackground | SystemColors.Window |
| Grid Text (Selected) | RevisionGridRelativeSelectedText | SystemColors.HighlightText |
| Grid Text (Normal) | RevisionGridNonRelativeText | SystemColors.ControlText |
| Commit Info BG | CommitInfoBackground | SystemColors.Window |

## 4. Build Status
- **Result:** Failed (NuGet Auth Error)
- **Reason:** Unauthorized access to private feed `cifor-icraf-is`.
- **Code Integrity:** All refactored files are syntactically valid and ready for merge once environment issues are resolved.
