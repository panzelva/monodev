how this should work:

1. user starts monodev with apps that he/she wants to develop
1. find monorepo root by finding the lock file (can be skipped by flag --root)
1. validate if the root is valid and resolve used package manager (yarn || npm || pnpm), user can override this by flag
1. resolve what monorepo tooling is user using (nx || turbo), user can override this by flag
1. generate dependency graph from monorepo tool
1. find all dependencies of provided apps that user wants to develop
1. check that there are no dependency loops and check that apps that user wants to develop are not dependent on each other
1. unless flag --skip-initial-build is provided, build all dependencies **(need to figure out how to specify build command per dependency)**
1. once dependencies are build, start dev mode for apps and start file watcher for dependencies and rebuild on change (both can be toggled by flag)
1. show interactive gui for these changes

libs to use:

- https://github.com/charmbracelet/bubbletea
- https://github.com/charmbracelet/lipgloss
- https://github.com/urfave/cli
- https://github.com/radovskyb/watcher or https://github.com/fsnotify/fsnotify

